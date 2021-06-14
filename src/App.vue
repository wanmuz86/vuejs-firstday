<template>
  <div class="container">
    <h2>Class notes!</h2>
    <h1>Hello World</h1>
    <p>My name is {{name}} and I stay in {{location}}</p>
    <p>I am {{age}} years old</p>
    <button v-on:click="sayHello">Say Hello</button>
    <h3>My student scores</h3>
     <ul>
      <li v-for="(score,index) in scores" :key="index">Item {{index}} is {{score}}</li>
    </ul>
    <input type="text" 
    placeholder="Enter your name" v-model="username"/>
    <p>Hello {{username}}</p>
    <hr/>
    <h2>Counter app!</h2>
    <p>{{number}}</p>
    <p class="text-danger" v-if="hasError">{{message}}</p>
    <button v-on:click="increment">Increment</button>
    <button v-on:click="decrement" v-bind:disabled="hasError">Decrement</button>
    <button v-on:click="reset">Reset</button>
    <hr/>
    <h2>Workout Of the Day exercise</h2>
    <div class="card bg-light p-5 mb-3">
    <h3>Add a new exercise</h3>
    <input type="text" placeholder="Enter Exercise name" 
    class="form form-control mb-3" v-model="newTodo.name"/>
    <select class="form form-control mb-3" 
    v-model="newTodo.difficulty">
      <option value="0">Select the difficulty</option>
      <option v-for="option in difficultyOptions" :key="option" v-bind:value="option">{{option}}</option>
    </select>
    <input type="text" placeholder="Enter Assignee name" 
    class="form 
    form-control mb-3" v-model="newTodo.assignee"/>
    <button class="btn btn-primary" v-on:click="addItem">Add</button>
    </div>
    <div class="card p-5 bg-light mb-3">
      <h3>The WODs</h3>
      <table class="table table-bordered table-striped table-hover">
        <thead>
          <tr class="bg-secondary text-light">
            <th>Exercise</th>
            <th>Difficulty</th>
            <th>Assignee</th>
          </tr>
    
        </thead>
        <tbody>
          <tr v-for="todo in todos" :key="todo.name">
            <td>{{todo.name}}</td>
            <td>{{todo.difficulty}}</td>
            <td>{{todo.assignee}}</td>
          </tr>
        </tbody>
      </table>
      </div> 
      <div class="card mb-3 bg-light p-5">
      <h3>Detail WOD</h3>
      <p>WOD name</p>
      <p>WOD difficulty</p>
      <p>WOD assignee</p>
      <div class="row">
      <div class="col-6">
      <button class="btn btn-success" 
      style="width:100%">Mark as Done</button>
      </div>
      <div class="col-6">
      <button class="btn btn-danger" 
      style="width:100%" >Delete</button>
      </div> 
      </div>
      </div> 
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      /// 5 main data types = String , number, boolean
      // array and object
      name:"Muzaffar",
      location:"Bangi",
      age:30,
      hasBreakfast:false,
      scores:[70,90,70,60,65],
      companyInfo:{"name":"Anak2U Sdn Bhd",
       "smmNum":"xxxxxxxx", 
      "location":"Bangi"},
      number:0,
      message:"Number cannot be less than 0",
      hasError:false,
      username:"",
      todos:[],
      newTodo:{
        "name":'',
        "difficulty":0,
        "assignee":''
      },
      difficultyOptions:[
          "Easy",
          "Medium",
          "Hard"
      ]
    }
  },
  methods:{
    sayHello: function(){
      alert("Hello World");
    },
    increment: function(){
      this.number++;
      this.hasError=false;
    },
    decrement:function(){
      if (this.number <= 0){
       this.hasError= true;
      }
      else {
      this.number--;
      }
    },
    reset:function(){
      this.number = 0;
      this.hasError=false;
    },
    addItem:function(){
      // TODO do verification first
      if (this.newTodo.name != "" && this.newTodo.difficulty == 0){
      this.todos.push(this.newTodo);
      this.newTodo = {
        "name":'',
        "difficulty":0,
        "assignee":''
      }
      }
      else {
        alert("Name cannot empty");
      }
    }
  }
}
</script>

<style>

</style>
