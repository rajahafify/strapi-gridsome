<template>
  <Layout>
    <div v-for="member in members" :key="member.id">
      <h2>Name: {{ member.attributes.name }}</h2>
      <p>Ic Number: {{ member.attributes.icNumber }}</p>
      <p>Email: {{ member.attributes.email }}</p>
      <p>Phone Number: {{ member.attributes.phoneNumber }}</p>
    </div>
  </Layout>
</template>

<script>
import axios from 'axios'
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  data() {
    return {
      members: null
    }
  },
  async mounted () {
    const { data } = await axios.get(process.env.GRIDSOME_API_URL + '/api/members')
    this.members = data.data
  }
}

</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
