<template>
  <div class="form-todo form-group">
  <p>
    <input placeholder="Nome" type="text" name="author" class="form-control" v-model="name" />
  </p>
    <p>
    <input placeholder="Idade" type="number" name="author" class="form-control" v-model="idade" />
  </p>
  <p>
    <textarea placeholder="Comentário" name="message"  class="form-control" v-model="message"></textarea>
  </p>
  <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        message: ''
      }
    },
    methods: {
      addComment() {
        if (this.message.trim() === '') {
          return;
        }
        this.$emit('add-todo', {
          name: this.name,
          idade: this.idade,
          message: this.message,
        });
        this.name = '';
        this.idade = '';
        this.message = '';
      }
    }
  }
</script>