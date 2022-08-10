<template>
  <svg version="1.1"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink" width="100%" height="100%" class="filterwrapper">
    <defs>

      <svg id="glitchmask-r" width="100%" height="100%" viewbox="0 0 100 100" preserveAspectRatio="none">
        <line class="top-r" x1="0" y1="0" x2="100%" y2="0"></line>
        <line class="bot-r" x1="0" y1="100%" x2="100%" y2="100%"></line>
      </svg>

      <svg id="glitchmask-g" width="100%" height="100%" viewbox="0 0 100 100" preserveAspectRatio="none">
        <line class="top-g" x1="0" y1="0" x2="100%" y2="0"></line>
        <line class="bot-g" x1="0" y1="100%" x2="100%" y2="100%"></line>
      </svg>

      <filter color-interpolation-filters="sRGB" id="filter" width="100%" heigth="100%" x="0" y="0">
        <feFlood flood-color="black" result="black" />

        <!-- red start -->
        <feFlood flood-color="red" result="REDTXT_FLOOD_10" />
        <feComposite operator="in" in="REDTXT_FLOOD_10" in2="SourceAlpha" result="REDTXT_COMP_20" />
        <feOffset in="SourceGraphic" dx="-2" dy="0" result="REDTXT_OFFSET_30" />
        <feMerge result="REDTXT_MERGE_40">
          <feMergeNode in="black" />
          <feMergeNode in="REDTXT_COMP_20" />
          <feMergeNode in="REDTXT_OFFSET_30" />
        </feMerge>
        <feImage preserveAspectRatio="none" id="mask-r" result="REDTXT_IMG_50" xlink:href="#glitchmask-r" />
        <feComposite in2="REDTXT_IMG_50" in="REDTXT_MERGE_40" operator="out" result="REDTXT_COMP_60" />
        <!-- red end -->

        <!-- green start -->
        <feFlood flood-color="limegreen" result="GREENTXT_FLOOD_10" />
        <feComposite operator="in" in="GREENTXT_FLOOD_10" in2="SourceAlpha" result="GREENTXT_COMP_20" />
        <feOffset in="SourceGraphic" dx="2" dy="0" result="GREENTXT_OFFSET_30" />
        <feMerge result="GREENTXT_MERGE_40">
          <feMergeNode in="black" />
          <feMergeNode in="GREENTXT_COMP_20" />
          <feMergeNode in="GREENTXT_OFFSET_30" />
        </feMerge>
        <feImage preserveAspectRatio="none" id="mask-g" result="GREENTXT_IMG_50" xlink:href="#glitchmask-g" />
        <feComposite in2="GREENTXT_IMG_50" in="GREENTXT_MERGE_40" operator="out" result="GREENTXT_COMP_60" />
        <!-- green end -->

        <feMerge result="MERGE_10">
          <feMergeNode in="SourceGraphic" />
          <feMergeNode in="REDTXT_COMP_60" />
          <feMergeNode in="GREENTXT_COMP_60" />
        </feMerge>

      </filter>
    </defs>
  </svg>

  <figure class="glitch-filter-example flex justify-center items-center">
    <div class="glitch-filter-example__filtered-text">
      <svg width="138" height="100" viewBox="0 0 138 100" fill="none"
        xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M28.125 9.375V90.625H109.375V9.375H28.125ZM25 0C21.5482 0 18.75 2.79822 18.75 6.25V93.75C18.75 97.2018 21.5482 100 25 100H112.5C115.952 100 118.75 97.2018 118.75 93.75V6.25C118.75 2.79822 115.952 0 112.5 0H25Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M118.75 37.5V62.5H128.125V37.5H118.75ZM115.625 28.125C112.173 28.125 109.375 30.9232 109.375 34.375V65.625C109.375 69.0768 112.173 71.875 115.625 71.875H131.25C134.702 71.875 137.5 69.0768 137.5 65.625V34.375C137.5 30.9232 134.702 28.125 131.25 28.125H115.625Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M9.375 37.5V62.5H18.75V37.5H9.375ZM6.25 28.125C2.79822 28.125 0 30.9232 0 34.375V65.625C0 69.0768 2.79822 71.875 6.25 71.875H21.875C25.3268 71.875 28.125 69.0768 28.125 65.625V34.375C28.125 30.9232 25.3268 28.125 21.875 28.125H6.25Z" fill="white"/>
        <path d="M43.75 39.0625C43.75 34.7478 47.2478 31.25 51.5625 31.25V31.25C55.8772 31.25 59.375 34.7478 59.375 39.0625V39.0625C59.375 43.3772 55.8772 46.875 51.5625 46.875V46.875C47.2478 46.875 43.75 43.3772 43.75 39.0625V39.0625Z" fill="white"/>
        <path d="M78.125 39.0625C78.125 34.7478 81.6228 31.25 85.9375 31.25V31.25C90.2522 31.25 93.75 34.7478 93.75 39.0625V39.0625C93.75 43.3772 90.2522 46.875 85.9375 46.875V46.875C81.6228 46.875 78.125 43.3772 78.125 39.0625V39.0625Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M50 56.25C50 66.6077 58.3954 75 68.75 75C79.1046 75 87.5 66.6077 87.5 56.25H50Z" fill="white"/>
      </svg>
    </div>
  </figure>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.filterwrapper {
    position: absolute;
    z-index: -1;
    pointer-events: none;
    opacity: 0;
}
.svgtext {
    display: block;
    position: relative;
    overflow: hidden;
    margin: 0 auto;
}
.intro {
    margin-bottom: 3em;
}
hr {
    height: 0;
    border-bottom: solid #cccccc 1px;
}
.glitch-filter-example {
    display: block;
    position: relative;
    text-align: center;
    margin: 0;
}
.glitch-filter-example__heading {
    margin: 0;
    margin-bottom: 1em;
    padding: 0;
    display: block;
    position: relative;
}
.glitch-filter-example__filtered-text {
    filter: url(#filter);
    fill: white;
    font-family: 'Share Tech Mono', sans-serif;
    font-size: 100px;
    text-align: center;
    margin: 0;
    padding: 0;
    display: block;
}
.top-r,
.bot-r,
.top-g,
.bot-g {
    stroke: #ffffff;
}
.top-r {
    stroke-width: 100px;
    animation: topani 3.5s linear infinite;
}
.bot-r {
    stroke-width: 100px;
    animation: botani 4s linear infinite;
}
.top-g {
    stroke-width: 50px;
    animation: topani 4s linear reverse infinite;
}
.bot-g {
    stroke-width: 50%;
    animation: botani 3.5s linear reverse infinite;
}
@mixin createRandomKeyframes( $numberOfKeys ) {
    $delta: round(100/$numberOfKeys);
    
    @for $i from 1 through $numberOfKeys {
        $time: ($i*$delta - random($delta)) +'%';
        #{$time} {
            stroke-width: random(200) + px;
        }
    }
}
@keyframes topani {
    @include createRandomKeyframes( 10 + random(10) );
}
@keyframes botani {
    @include createRandomKeyframes( 10 + random(10) );
}
</style>