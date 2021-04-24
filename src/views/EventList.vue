<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="eventwa in events" :key="eventwa.id" :event="eventwa" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
// import axios from 'axios'
import EventService from '@/services/EventService.js'

export default {
  name: "EventList",
  components: {
    EventCard  // register it as a child component
  },
  data() {
    return {
      events: null
    };
  },
  created() {
    // get events from mock db when component is created

    // axios.get('https://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/events')
    //   .then(response => {
    //     this.events = response.data
    //   })
    //   .catch(error => {
    //     console.log(error)
    //   })

    EventService.getEvents()
      .then(response => {
        this.events = response.data
      })
      .catch(error => {
        console.log(error)
      })
  }
};
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
