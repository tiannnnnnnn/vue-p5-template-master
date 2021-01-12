<template>
  <div class="container">
    <div class="p5Canvas"></div>
  </div>
</template>

<script>
import P5 from 'p5';

export default {
  data() {
    return {
      p5Canvas: null,
    }
  },
  created() {
    const sketch = p5 => {
        let w = 300;
        let h = 300;

        // let w = window.innerWidth;
        // let h = window.innerHeight;

        p5.setup = () => {
            p5.createCanvas(w, h, p5.WEBGL);
        };

        p5.draw = () => {
            // call your method:
            p5.changeBG(p5.mouseX, p5.mouseY);
            
            // p5.background(33, 33, 33);
            //p5.ellipse(p5.mouseX, p5.mouseY, 100);
            // let step = frameCount % 20;
            // let angle = map(step, 0, 20, 0, TWO_PI);
            // let cos_a = cos(angle);
            // let sin_a = sin(angle);
            // p5.background(200);
            p5.translate(75, 0);
            // sketch.applyMatrix(cos_a, sin_a, -sin_a, cos_a, 0, 0);

            // for(var i=0;i<11;i++){

            //   for(var j=0;j<11;j++){

                p5.push();
                p5.translate(-w / 4, 0, 0);
                p5.rotate(p5.frameCount * 0.02);
                // p5.rotateY(p5.frameCount * 0.02);
                // p5.specularMaterial(250);
                for(var i=0;i<11;i++){
                  for(var j=0;j<11;j++){
                    p5.rect(i*30, j*30, 20, 30);
                    p5.fill(135, 206, 250);
                     
                    
                  }
                }
                p5.pop();
            //   }
            // }
    
        };

        // create methods:
        p5.changeBG = (x, y) => {
          let _x = p5.map(x, 0, w, 0, 255);
          let _y = p5.map(y, 0, h, 0, 255);
          p5.background(_x, _y, 33);
        }
    }

    this.p5Canvas = new P5(sketch, 'p5Canvas');
  },
  unmounted () {
    this.p5Canvas = null;
  },
}
</script>

<style>
#p5Canvas {
  width: 100vw;
  position: relative;
}

main {
  margin: 0 auto;
  width: 90vw;
}
</style>
