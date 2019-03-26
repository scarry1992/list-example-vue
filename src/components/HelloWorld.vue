<template>
    <div style="width: 300px; margin: 0 auto;">
        <VirtualList class="list"
            :size="50"
            :remain="remain"
            :bench="bench"
            :start="start"
            :item="item"
            :itemcount="count"
            :itemprops="itemBinding"
        ></VirtualList>
        <!-- <VirtualList class="list"
            :size="50"
            :remain="remain"
            :bench="bench"
            :start="start"
        >
            <item v-for="(item, index) in itemdata" :key="index" :index="index" />
        </VirtualList> -->
    </div>
</template>

<script>
import Item from './Item'
import VirtualList from 'vue-virtual-scroll-list'
var TenThousand = 10000
var INIT_COUNT = TenThousand * 50
export default {
  name: 'finite-test-item-mode',
  components: {
    // Item,
    VirtualList
  },
  data () {
    let items = []
    for (let i = 0; i < 500000; i++) {
      items[i] = {index: i}
    }
    return {
      count: INIT_COUNT,
      start: 0,
      remain: 6,
      bench: 6,
      itemdata: items,
      item: Item
    }
  },
  methods: {
    // simple variable test
    // variableHeight() {
    //     return 45;
    // },
    itemBinding (idx) {
      return {
        key: 'item' + idx,
        props: {
          index: idx
        }
      }
    }
  }
}
</script>

<style>
    .scrollToIndex {
        padding-bottom: 20px;
    }
    .op {
        padding-bottom: 1em;
    }
    .op-item {
        padding: .2em 0;
    }
    label {
        display: inline-block;
        width: 100px;
        padding-right: 1em;
        text-align: right;
    }
    input {
        outline: none;
        padding: .5em;
        width: 80px;
    }
    input {
        outline: none;
        padding: .4em .5em;
        width: 105px;
        height: 16px;
        border-radius: 3px;
        border: 1px solid;
        border-color: #dddddd;
        font-size: 16px;
        -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none;
    }
    input:focus {
        border-color: #6495ed;
    }
    small {
        color: #999;
    }
    .list {
        background: #fff;
        border-radius: 3px;
        border: 1px solid #ddd;
        -webkit-overflow-scrolling: touch;
        overflow-scrolling: touch;
    }
    .source {
        text-align: center;
        padding-top: 20px;
    }
    .source a {
        color: #999;
        text-decoration: none;
        font-weight: 100;
    }
    @media (max-width: 640px) {
        small {
            display: none;
        }
    }
</style>
