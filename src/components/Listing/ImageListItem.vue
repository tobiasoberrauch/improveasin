<template>
  <b-card :class="{ active: selectedItems.includes(data.objectId) }" no-body>
    <div class="position-relative">
      <router-link :to="`?p=${data.objectId}`" class="w-40 w-sm-100">
        <img :src="data.image.url" class="card-img-top" :alt="data.title" />
      </router-link>
      <b-badge
        pill
        :variant="data.statusColor"
        class="position-absolute badge-top-left"
        >{{ data.status }}</b-badge
      >
    </div>
    <b-card-body>
      <b-row>
        <b-colxx xxs="2">
          <b-form-checkbox
            :checked="selectedItems.includes(data.objectId)"
            @click.prevent="toggleItem($event, data.objectId)"
            class="itemCheck mb-0"
          />
        </b-colxx>
        <b-colxx xxs="10" class="mb-3">
          <h6 class="mb-4 card-subtitle">{{ data.title }}</h6>
          <p class="text-muted text-small mb-0 font-weight-light card-text">
            {{ data.date }}
          </p>
        </b-colxx>
      </b-row>

      <button
        type="button"
        class="btn top-right-button btn-primary btn-lg"
        @click.prevent="toggleModal($event, data)"
      >
        Edit
      </button>
    </b-card-body>
  </b-card>
</template>

<script>
export default {
  props: ["data", "selectedItems"],
  methods: {
    toggleItem(event, itemId) {
      this.$emit("toggle-item", event, itemId);
    }
  }
};
</script>
