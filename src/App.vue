<script setup>
import { ref } from "vue";

const images = ref([
  "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
  "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
  "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
  "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
]);

const currentIndex = ref(0);

function setImage(image) {
  currentIndex.value = images.value.indexOf(image);
}

function next() {
  currentIndex.value = (currentIndex.value + 1) % images.value.length;
}

function prev() {
  currentIndex.value =
    (currentIndex.value - 1 + images.value.length) % images.value.length;
}
</script>

<template>
  <div>
    <div>
      <!-- Image Carousel Component -->
      <div class="carousel">
        <div
          class="carousel-inner"
          :style="{ transform: 'translateX(-' + currentIndex * 100 + '%)' }"
        >
          <div
            v-for="(image, index) in images"
            :key="index"
            class="carousel-slide"
          >
            <img
              :src="image"
              alt="Image Slide"
              class="w-full h-full object-cover"
            />
          </div>
        </div>
        <button @click="prev" class="carousel-button prev-button">
          Previous
        </button>
        <button @click="next" class="carousel-button next-button">Next</button>
      </div>
    </div>
  </div>
</template>

<style>
.carousel {
  position: relative;
  overflow: hidden;
}

.carousel-inner {
  display: flex;
  transition: transform 0.3s ease-in-out;
}

.carousel-slide {
  flex: 0 0 100%;
}

.carousel-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  padding: 8px 12px;
  background-color: #333;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.prev-button {
  left: 16px;
}

.next-button {
  right: 16px;
}
</style>
