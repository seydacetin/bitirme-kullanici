<template>
  <v-card id="account-setting-card">
    <!-- tabs -->
    <v-tabs
      v-model="tab"
      show-arrows
    >
      <v-tab
        v-for="tab in tabs"
        :key="tab.icon"
      >
        <span>{{ tab.title }}</span>
      </v-tab>
    </v-tabs>

    <!-- tabs item -->
    <v-tabs-items v-model="tab">
      <v-tab-item>
        <bildirim-listesi> </bildirim-listesi>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>

<script>
import { ref } from '@vue/composition-api'

import BildirimListesi from './BildirimListesi.vue'

export default {
  components: {
    BildirimListesi,
  },
  created() {
    if (localStorage.value === 'false') {
      this.$router.push('/pages/login')
    }
  },
  setup() {
    const tab = ref('')

    const tabs = [
      { title: 'Bildirim Listesi' },
    ]

    return {
      tab,
      tabs,
    }
  },
}
</script>
