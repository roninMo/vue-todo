<template>
  <form @submit.prevent="addTodo">
    <input type="text" v-model="title" name="title" placeholder="Enter todo" />
    <input type="submit" value="Submit" class="btn" />
  </form>
</template>

<script>
// import uuid from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false,
      };
      // Send up to parent $emit functions
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>
