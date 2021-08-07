<template>
  <div id="container" class="bg-success">
    <div id="quote-box" class="bg-light mx-auto rounded px-5 py-4">
      <div class="row mt-2">
        <div class="col">
          <h2 id="text" class="text-center">
            <i class="bi bi-chat-right-quote fs-2"></i>
            {{ text }}
          </h2>
        </div>
      </div>
      <div id="author" class="row mt-2">
        <div class="col text-end">- {{ author }}</div>
      </div>
      <div class="row mt-4 mb-3">
        <div class="col-8">
          <a
            id="tweet-quote"
            href="twitter.com/intent/tweet"
            class="btn btn-success"
          >
            <i class="bi bi-twitter"></i>
          </a>
          <button class="btn btn-success ms-2">
            <i class="bi bi-facebook"></i>
          </button>
        </div>
        <div class="col-4 text-end">
          <button id="new-quote" @click="fetchQuote" class="btn btn-success">
            New quote
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  beforeCreate: async function() {
    const res = await fetch("https://api.quotable.io/random");
    const quote = await res.json();
    this.author = quote.author;
    this.text = quote.content;
  },
  methods: {
    async fetchQuote() {
      const res = await fetch("https://api.quotable.io/random");
      const quote = await res.json();
      this.author = quote.author;
      this.text = quote.content;
    }
  },
  data() {
    return {
      text: "Random Quote.",
      author: "Author"
    };
  }
};
</script>

<style>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.5.0/font/bootstrap-icons.css");
#container {
  width: 100vw;
  height: 100vh;
  padding-top: 30vh;
}
#quote-box {
  width: 550px;
}
</style>
