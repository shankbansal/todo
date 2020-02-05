<template>
  <div class="md-layout md-gutter md-alignment-center">
    <div class="md-layout-item md-large-size-60 md-medium-size-60 md-small-size-80 md-xsmall-size-80">
      <h1>To-do List</h1>
      <md-field>
        <md-input v-model="currentTodo" @keydown.enter="addTodo()" placeholder="Add to-do"></md-input>
      </md-field>

      <h3>To-do Items</h3>
      <ul class="todos">
        <li v-for="todo in todos" :key="todo.id">
          <div style="display:flex;align-items:center">
          <span>{{ todo.label }}</span>
          <md-button class="md-raised md-primary md-dense" @click="markCompleted(todo)">Mark Completed</md-button>
          <md-button  class="md-raised md-accent md-dense" @click="removeTodo(todo)">Remove</md-button>
          </div>
        </li>
      </ul>
      <h3>Completed Items</h3>
      <ul class="todos">
        <li v-for="todo in completedTodo" :key="todo.id">
          <div style="display:flex;align-items:center">
          <span>{{ todo.label }}</span>
          <md-button class="md-raised md-accent md-dense" @click="removeFromCompleted(todo)">Remove</md-button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
      completedTodo: [],
      currentTodo: ""
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: this.todos.length,
        label: this.currentTodo,
        completed: false
      });
      this.currentTodo = "";
    },
    removeTodo(todo) {
      var index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
    },
    markCompleted(todo) {
      var index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
      this.completedTodo.push(todo);
    },
    removeFromCompleted(todo) {
      var index = this.completedTodo.indexOf(todo);
      this.completedTodo.splice(index, 1);
    }
  }
};
</script>

<style>
</style>