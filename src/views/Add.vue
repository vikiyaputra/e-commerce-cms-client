<template>
<div>
  <Navbar></Navbar>
  <div class = "container d-flex justify-content-center align-items-center">
    <div class= "col-8">
      <h1 class= "mt-3">Add new Product</h1>
      <form @submit.prevent="add" >
        <div class="form-group">
          <label for="exampleInputEmail1">Name of Product</label>
          <input v-model="name" type="text" class="form-control" id="editEmail" aria-describedby="emailHelp" required>
        </div><br>
        <div class="form-group">
          <label for="exampleInputPassword1">Image URL</label>
          <input v-model="image_url" type="url" class="form-control" id="exampleInputPassword1" required>
        </div><br>
        <div class="form-group">
          <label for="exampleInputEmail1">Price</label>
          <input v-model="price" type="number" class="form-control" id="editEmail" aria-describedby="emailHelp" required>
        </div><br>
        <div class="form-group">
          <label for="exampleInputEmail1">Stock</label>
          <input v-model="stock" type="number" class="form-control" id="editEmail" aria-describedby="emailHelp" required>
        </div><br>
        <div class="container d-flex justify-content-center">
          <button type="submit" class="btn btn-primary mx-3">Add Product</button>
          <button type="button" class="btn btn-danger mx-3" @click.prevent="toHome">Back</button>
        </div>
      </form>
    </div>
  </div>
</div>
</template>

<script>
// import axios from '../axios/axios.js'
import Navbar from '../components/Navbar.vue'
// import Swal from 'sweetalert2'

export default {
  name: 'Add',
  data: function () {
    return {
      name: '',
      image_url: '',
      price: 0,
      stock: 0
    }
  },
  components: { Navbar },
  methods: {
    add () {
      const payload = { name: this.name, image_url: this.image_url, price: Number(this.price), stock: Number(this.stock) }
      this.$store.dispatch('addProduct', payload)
    //   axios.post('/products', payload, {
    //     headers: {
    //       access_token: localStorage.getItem('access_token')
    //     }
    //   })
    //     .then(data => {
    //       this.name = ''
    //       this.image_url = ''
    //       this.price = 0
    //       this.stock = 0
    //       this.$router.push('/products')
    //       Swal.fire({
    //         position: 'top-end',
    //         icon: 'success',
    //         title: 'Product Added',
    //         showConfirmButton: false,
    //         timer: 1500
    //       })
    //     })
    //     .catch(err => {
    //       console.log(err.response.data)
    //     })
    // },
    },
    toHome () {
      this.$router.push('/products')
    }
  }
}
</script>

<style>

</style>
