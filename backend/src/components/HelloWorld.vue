<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})


// MOSSY SHIT


</script>


<script>
import * as THREE from '../../node_modules/three'
import { GLTFLoader } from '../../node_modules/three/examples/jsm/loaders/GLTFLoader.js'
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

const renderer = new THREE.WebGLRenderer();
//renderer.setSize( window.innerWidth*0.2, window.innerHeight*0.2 );

// NOTE: this add crab to page but can't place it properly
document.body.prepend( renderer.domElement );


/* hiding cube for now
const geometry = new THREE.BoxGeometry( 1, 1, 1 );
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
const cube = new THREE.Mesh( geometry, material );
scene.add( cube );
*/
camera.position.z = 5;
camera.position.x = 0;
camera.position.y = 5;
/*
function animate() {
	requestAnimationFrame( animate );
  cube.rotation.x += 0.01;
cube.rotation.y += 0.01;
	renderer.render( scene, camera );
}
animate();
*/


/// DIFFERENT SHIT - LOADING GLTF

const loader = new GLTFLoader();

loader.load( './src/assets/dome-krab.gltf', function ( gltf ) {

	scene.add( gltf.scene );
  renderer.render( scene, camera );

}, undefined, function ( error ) {

	console.error( error );

} );
// NOTE: attempting to use renderer as a component
export default {
  components: {
    renderer,
  }
  }
</script>




<template>
 
  <div class="greetings">
    <renderer />
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
