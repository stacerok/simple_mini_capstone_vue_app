<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div>
      <div v-for="product in products" v-bind:key="product">
        <h3>{{ product.name }}</h3>
        {{ product.description }}
        <br />
        ${{ product.price }}
      </div>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to my Shop.",
      products: [],
    };
  },
  created: function() {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("/api/products").then((response) => {
        this.products = response.data;
        console.log("All Products:", this.products);
      });
    },
  },
};
</script>
