<template>
  <div>
    <input type="text" v-model="message" />
    <button class="btn" @click="send">Отправить</button>
  </div>
</template>

<script>
const { io } = require("socket.io-client");
const socket = io("http://localhost:3001");

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      message: null,
    };
  },
  methods: {
    send() {
      socket.emit("message", this.message);
    },
  },
};
</script>

