<template>

  
  <h3>Log Hours:</h3>
  
  <form @submit.prevent="submitDatabase">
      <label>Username:</label>
      <input type="username" required v-model="posts.username">
      
      <label>Category:</label>
      <input type="category" required v-model="posts.category">

      <label>Hours:</label>
      <input type="number" required v-model="posts.hours">

      <label>Date:</label>
      <input type="date" required v-model="posts.date">

    <div class="submit">
        <button>Log Information</button>
    </div>
      

  </form>
    

</template>

<script>
import axios from 'axios';
import {mapState} from "vuex";
export default {
    name: 'enterInfo',
    data() {
        return {
            posts:{
                username: "",
                category : "",
                hours: "",
                date: ""  
            }
            
        }
    },
    computed : mapState(["username"]),
    methods: {
        submitDatabase: async function(){
            console.log('form submitted');
            console.log(this.username);
            console.log(this.posts.date)
            await axios.post("http://127.0.0.1:8081/inputdata", this.posts);
               
        }
    }
}
</script>

<style>
form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
button {
    background: #001f39;
    border: 0;
    padding: 10px 20px;
    margin-top:20px;
    color: #dfdfdf;
    border-radius: 20px;
}
.submit {
    text-align: center;
}
</style>