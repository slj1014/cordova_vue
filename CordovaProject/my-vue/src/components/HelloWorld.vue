<template>
  <div class="hello">
    <van-button type="info" @click="show()">显示设备信息</van-button>
    <span>{{msg}}</span>
    <van-button type="warning" @click="shake()">点击振动</van-button>
    <van-button type="primary" @click="cameraTakePicture()">点击拍照</van-button>
    <img id = "myImage"></img>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      "msg":""
    }
  },
  methods:{
    shake(){
      navigator.vibrate(3000);
    },
    show(){
      this.msg="Cordova 版本: " + device.cordova + "\n" +
        "设备类型: " + device.model + "\n" +
        "设备平台: " + device.platform + "\n" +
        "设备UUID: " + device.uuid + "\n" +
        "设备版本: " + device.version;
    },
    cameraTakePicture(){
      navigator.camera.getPicture(onSuccess, onFail, {
        quality: 50,
        destinationType: Camera.DestinationType.DATA_URL
      });

      function onSuccess(imageData) {
        var image = document.getElementById('myImage');
        image.src = "data:image/jpeg;base64," + imageData;
      }

      function onFail(message) {
        alert('Failed because: ' + message);
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
