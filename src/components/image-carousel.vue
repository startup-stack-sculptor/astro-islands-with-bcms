<script setup>
import { bcms } from "../bcms-client";
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

const props = defineProps({
  collection: {
    type: Array,
    required: true,
  },
});

const config = {
  height: 600,
  itemsToShow: 1,
  gap: 5,
};
</script>

<template>
  <Carousel v-bind="config">
    <Slide v-for="media in collection" :key="media._id">
      <img
        :src="`${bcms.cmsOrigin}${bcms.media.toUri(media._id, media.name)}`"
        alt="media.name"
      />
    </Slide>

    <template #addons>
      <Navigation />
      <Pagination />
    </template>
  </Carousel>
</template>

<style>
.carousel {
  --vc-pgn-background-color: rgba(255, 255, 255, 0.7);
  --vc-pgn-active-color: rgba(255, 255, 255, 1);
  --vc-nav-background: rgba(255, 255, 255, 0.7);
  --vc-nav-border-radius: 100%;
}

img {
  border-radius: 8px;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
