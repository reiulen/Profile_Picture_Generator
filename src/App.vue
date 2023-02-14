<template>
  <div id="app">
    <div>
      <form @submit="getPosts">
        <div>
          <input class="input form-control" type="text" v-model="keyword" />
        </div>
        <div class="flex justify-center">
          <button class="btn btn-success">Buat Profil Picture!</button>
        </div>
        <div class="flex justify-center">
          <div v-if="image !== ''" class="image-thumbnail">
            <img :src="image" alt="image" />
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      keyword: "",
      image: "",
    };
  },
  methods: {
    async getPosts(e) {
      e.preventDefault();

      if(this.keyword === "") {
        alert("Masukkan keyword terlebih dahulu!")
        return false;
      }

      this.image = `https://robohash.org/${this.keyword ?? ""}`;
    },
  },
};
</script>

<style>
body {
  background-color: #e0ffff;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 40px;
}

.flex {
  display: flex;
}

.justify-center {
  justify-content: center;
}

.input.form-control {
  min-width: 350px;
  margin-bottom: 10px;
  min-height: 20px;
  border: 1px solid rgb(224, 224, 224);
  background-color: white;
  border-radius: 6px;
  padding: 10px;
}

.input.form-control:focus {
  outline: none;
}

.btn.btn-success {
  min-height: 30px;
  background-color: #28a745;
  border: none;
  color: white;
  padding: 10px 15px;
  border-radius: 4px;
  cursor: pointer;
}

.btn.btn-success:focus {
  border-radius: 4px;
  outline: 4px solid #8dbb96;
}

.image-thumbnail { 
  margin-top: 30px;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 200px;
  width: 200px;
  border-radius: 50%;
  overflow: hidden;
  border: 1px solid rgb(209, 209, 209);

}

.image-thumbnail img {
  height: 180px;
  border-radius: 50%;
}
</style>
