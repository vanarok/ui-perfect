<script setup>
import { ref } from 'vue';

const data = ref([
  {
    title: 'Photography',
    images: ['image1', 'image1.1'],
    text: 'Every photograph we produce finds the beauty in your property while serving as a profitable asset.',
    list: ['Drone Photography', 'Interiors', 'Exteriors / Architectural'],
  },
  {
    title: 'Virtual Staging',
    images: ['image2'],
    text: 'Our staging will help you sell the potential of your space. \n We can work off of our own photography or photos you provide.',
  },
  {
    title: 'Renderings',
    images: ['image6'],
    text: 'Renderings are the gold standard in pre-construction marketing.',
    list: ['Interiors', 'Exteriors'],
  },
  {
    title: 'Interactive Tours',
    images: ['image5'],
    text: 'Give your audience the ability to explore your property without requiring in-person travel.',
    list: ['Matterport', 'Video Walkthroughs'],
  },
  {
    title: 'Floor Plans',
    images: ['image4'],
    text: 'We produce laser-precise floor plans faster than any other service.',
    list: ['On-site Measure', '2D Floor Plans', '3D Floor Plans'],
  },
  {
    title: 'Video',
    images: ['image3'],
    text: 'Video content has higher engagement and will help your property stand out online.',
    list: ['Drone Cinematography', 'Interiors', 'Exteriors / Architectural'],
  },
]);

function getImageUrl(name) {
  return new URL(`./assets/${name}.png`, import.meta.url).href;
}
const goToUpwork = () =>
  (window.location = 'https://www.upwork.com/freelancers/~01d481153ecadb517e');

const cardBodyStyle = {
  padding: '0',
};
</script>

<template>
  <el-config-provider namespace="ep">
    <div class="header-1 mt-27">
      <h1 class="md:ma-0 md:pa-0">
        We make creative media that
        <span color="#506BCA">adds value</span>
      </h1>
    </div>
    <div class="main my-20">
      <div class="container">
        <div class="posts">
          <el-card
            v-for="post in data"
            class="post"
            shadow="hover"
            :body-style="cardBodyStyle"
          >
            <div class="post-container">
              <div class="post-images">
                <el-image
                  v-for="image in post.images"
                  :src="getImageUrl(image)"
                  fit="none"
                >
                  <template #placeholder>
                    <div class="image-placeholder">Loading...</div>
                  </template>
                </el-image>
              </div>

              <div class="post-body">
                <div class="header-2" v-text="post.title" />
                <ul v-if="post.list">
                  <li v-for="list in post.list" v-text="list" />
                </ul>
                <div class="text" v-text="post.text"></div>
              </div>
            </div>
          </el-card>
        </div>

        <div class="actions">
          <button
            style="cursor: pointer"
            @click="goToUpwork"
            class="start-button"
          >
            GET STARTED
          </button>
        </div>
      </div>
    </div>
  </el-config-provider>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@600&family=Poppins:wght@700&family=Nunito+Sans:wght@700&display=swap');

#app {
  color: var(--ep-text-color-primary);
}

body {
  background: #e5e5e5;
  overflow-x: hidden;
}

h1 {
  font-family: 'Poppins', sans-serif;
  font-display: block;
  font-style: normal;
  font-weight: 700;
  font-size: 56px;
  line-height: 55px;
  width: 730px;
}

.header-1 {
  display: flex;
  justify-content: center;
  text-align: center;
  letter-spacing: -0.01em;

  color: #1b264f;
}

.header-2 {
  font-family: 'Poppins', sans-serif;
  font-display: block;
  font-style: normal;
  font-weight: 700;
  font-size: 24px;
  line-height: 32px;
  margin-bottom: 12px;

  font-feature-settings: 'salt' on, 'liga' off;

  color: #353844;
}
.main {
  display: flex;
  justify-content: center;
}
.posts {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 40px 30px;
}
.post {
  display: flex;
  flex-direction: row;

  height: 100%;

  border-radius: 8px;
  border: 0px;
  padding-right: 50px;
}
.post-container {
  display: flex;
  flex-direction: row;
}

.post-images {
  display: flex;
  gap: 3px;
  height: 100%;
  flex-direction: column;
  margin-right: 34px;
}
.image-placeholder {
  width: 183.5px;
  height: 336px;
  background-color: #fff;
}

.post-body {
  width: 190px;
  height: 149px;
  margin-top: 40px;
}
.text {
  white-space: pre-line;
  font-family: 'Nunito Sans';
  font-style: normal;
  font-weight: 600;
  font-size: 15px;
  line-height: 24px;

  font-feature-settings: 'salt' on, 'liga' off;

  color: #353844;
}
ul {
  list-style: none;
}
li {
  font-family: 'Nunito Sans';
  font-style: normal;
  font-weight: 700;
  font-size: 15px;
  line-height: 26px;
}
ul li::before {
  color: #d2ad81;
  content: '\2022';
  font-weight: bold;
  display: inline-block;
  width: 14px;
  margin-left: -2.7em;
}
.start-button {
  width: 315px;
  height: 60px;
  background: #1b264f;
  border-radius: 12px;
  font-family: 'Poppins';
  font-style: normal;
  font-weight: 700;
  font-size: 17px;
  line-height: 40px;
  color: #ffffff;
  border-color: #1b264f;
  text-align: center;
  margin-top: 80px;
  align-items: center;
  padding: 0px 70px;
  text-align: center;
  letter-spacing: 0.2em;
  text-transform: uppercase;
}
.start-button:hover {
  background: #3f4d81;
}
.actions {
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>
