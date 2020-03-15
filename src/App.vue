<template>
  <div id="app">
    <h2>deep watch</h2>
    <div v-for="user in users" :key="user.id">
      <input type="text" v-model = user.name>
    </div>
    <button @click="users.push({id:users.length+1, name: 'hello '+parseInt(users.length+1)})">add user</button>
   
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {

  },
  data(){
    return{
      users: [
        {id:1, name: 'sourya'},
        {id:2, name: 'rama'},
        {id:3, name: 'john'}
      ]
    }
  },
  // immediate- to execute handler as soon as component/page loaded
  // without deep - it will watch/execute handler when there is  change in no. of items in array but not when a property value of an obj in array changes
  // with deep- it will watch/execute handler when there is  change in no. of items, and change in value of propery of any obj in array
  // newval==oldval in both cases as the reference to array is same that vue watches.
  watch: {
    users:{
      deep: true,
      // immediate: true,
      handler(newval,oldval){
        // doSomething 
        console.log('The list of users has changed!\n newval ',newval, '\noldval ',oldval);
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
