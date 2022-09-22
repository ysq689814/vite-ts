<template>
    <div style="margin-left:30px;" class="tree">
        <div :key="index" v-for="(item,index) in data">
            <div @click='clickItem(item)'>{{item.name}} </div>
            <TreeItem @on-click='clickItem' v-if='item?.children?.length' :data="item.children"></TreeItem>
        </div>
    </div>
</template>
<script setup lang="ts">
import { ref, watch, reactive, watchEffect, onBeforeMount } from 'vue'
type TreeList = {
  name: string;
  icon?: string;
  children?: TreeList[] | [];
};
 
type Props<T> = {
  data?: T[] | [];
};
 
defineProps<Props<TreeList>>();
 
const clickItem = (item: TreeList) => {
  console.log(item)
}
</script>