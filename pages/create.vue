<template>
  <main class="min-h-screen">
    <div class="page-container">
      <div class="event-page-content-wrapper zm-container">
        <div class="event-page-left min-width-0">
          <div class="photo-container">
            <input
              accept="image/*,.jpg,.jpeg,.png,.gif,.webp"
              type="file"
              tabindex="-1"
              class="jsx-1991948234"
              style="display: none"
            />
            <div class="img-aspect-ratio">
              <img
                src="https://images.lumacdn.com/cdn-cgi/image/format=auto,fit=cover,dpr=2,quality=75,width=400,height=400/gallery-images/nu/68ed8d78-9f69-4994-a122-d7e1888ef0b5"
                fetchpriority="auto"
                loading="eager"
              />
            </div>
            <div class="button-icon">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
                <path
                  fill="currentColor"
                  fill-rule="evenodd"
                  d="M8 .25h-.042c-1.369 0-2.454 0-3.32.088-.888.09-1.629.28-2.277.713a4.75 4.75 0 0 0-1.31 1.31c-.434.648-.623 1.39-.713 2.277C.25 5.504.25 6.589.25 7.958v.084c0 1.369 0 2.454.088 3.32.09.888.28 1.629.713 2.277.346.519.791.964 1.31 1.31.648.434 1.39.623 2.277.713.866.088 1.951.088 3.32.088h.084c1.369 0 2.454 0 3.32-.088.888-.09 1.629-.28 2.277-.712a4.753 4.753 0 0 0 1.31-1.311c.434-.648.623-1.39.713-2.277.088-.866.088-1.951.088-3.32v-.084c0-1.369 0-2.454-.088-3.32-.09-.888-.28-1.629-.712-2.277a4.751 4.751 0 0 0-1.311-1.31c-.648-.434-1.39-.623-2.277-.713C10.496.25 9.411.25 8.042.25H8Zm2.32 8.535c.156-.21.735-.868 1.486-.4.478.295.88.694 1.31 1.12.164.164.28.35.359.549.234.6.112 1.323-.138 1.918a2.589 2.589 0 0 1-1.583 1.479c-.318.104-.652.149-.984.149h-5.9c-.587 0-1.106-.14-1.532-.403-.267-.165-.314-.545-.116-.791.33-.412.657-.825.986-1.242.628-.797 1.051-1.029 1.522-.826.19.084.382.21.579.343.525.357 1.255.847 2.216.315.658-.369 1.04-1 1.372-1.551l.006-.01.07-.115a6.75 6.75 0 0 1 .347-.535ZM3.8 5.55c0-.965.784-1.75 1.75-1.75.964 0 1.748.785 1.748 1.75S6.514 7.3 5.55 7.3C4.584 7.3 3.8 6.515 3.8 5.55Z"
                ></path>
              </svg>
            </div>
          </div>
          <button type="button" class="create-theme-button">
            <img
              src="https://images.lumacdn.com/themes/thumb/minimal.jpg"
              class="jsx-1511002150"
            />
            <div class="texts">
              <div class="h2">主题</div>
              <div class="h3">极简风</div>
            </div>
            <div class="icon">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                viewBox="0 0 24 24"
              >
                <path d="M17 3a2.828 2.828 0 1 1 4 4L7.5 20.5 2 22l1.5-5.5L17 3z"></path>
              </svg>
            </div>
          </button>
        </div>
        <div class="event-page-right min-width-0 flex-1">
          <UPopover :popper="{ placement: 'bottom-start' }">
            <UButton
              icon="i-heroicons-globe-alt"
              size="sm"
              color="gray"
              variant="soft"
              label="公开"
              :trailing="false"
            >
              <template #trailing>
                <UIcon name="i-heroicons-chevron-down" />
              </template>
            </UButton>

            <template #panel="{ close }">
              <UCommandPalette>
                <template #empty-state>
                  <div class="flex flex-col items-center justify-center py-6 gap-3">
                    <span class="italic text-sm">Nothing here!</span>
                  </div>
                </template>
              </UCommandPalette>
            </template>
          </UPopover>

          <UInput
            size="xl"
            color="red"
            variant="none"
            placeholder="活动名称"
            model-value=""
          />
          <div class="flex-column gap-3">
            <div class="time-picker flex-1">
              <div class="box1 relative flex-1">
                <div class="timeline"></div>
                <div class="start-row flex-baseline">
                  <div class="dot"></div>
                  <div class="label nowrap flex-1">开始</div>
                  <UPopover :popper="{ placement: 'bottom-start' }">
                    <div class="date-input">
                      <input
                        type="text"
                        class="dt-input"
                        :value="dayjs(startDate).format('MMMDD日dddd')"
                      />
                    </div>
                    <template #panel="{ close }">
                      <DatePicker v-model="startDate" @close="close" />
                    </template>
                  </UPopover>
                  <div class="divider"></div>
                  <div class="time-input">
                    <USelectMenu
                      v-slot="{ open }"
                      class="dt-input"
                      v-model="StartTimeSelected"
                      :options="StartTimePeople"
                    >
                      <input
                        type="time"
                        placeholder="HH:MM"
                        class="dt-input"
                        :value="StartTimeSelected"
                      />
                    </USelectMenu>
                  </div>
                </div>
                <div class="end-row flex-baseline">
                  <div class="dot"></div>
                  <div class="label nowrap flex-1">结束</div>

                  <UPopover :popper="{ placement: 'bottom-start' }">
                    <div class="date-input">
                      <input
                        type="text"
                        class="dt-input"
                        :value="dayjs(endDate).format('MMMDD日dddd')"
                      />
                    </div>
                    <template #panel="{ close }">
                      <DatePicker v-model="endDate" @close="close" />
                    </template>
                  </UPopover>

                  <div class="divider"></div>
                  <div class="time-input">
                    <USelectMenu
                      class="dt-input"
                      v-model="EndTimeSelected"
                      :options="EndTimePeople"
                    >
                      <input
                        type="time"
                        placeholder="HH:MM"
                        class="dt-input"
                        :value="EndTimeSelected"
                      />
                    </USelectMenu>
                  </div>
                </div>
              </div>
              <UPopover :popper="{ arrow: true, placement: 'bottom-end' }">
                <div class="tz-input animated">
                  <div class="lux-menu-trigger-wrapper cursor-pointer full-width">
                    <div class="tz-display text-secondary-alpha">
                      <div class="icon">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
                          <path
                            fill="currentColor"
                            fill-rule="evenodd"
                            d="M9.394 12.674c-.604 1.208-1.178 1.42-1.394 1.42-.216 0-.79-.212-1.394-1.42-.491-.982-.85-2.368-.932-3.97h4.652c-.082 1.602-.44 2.988-.932 3.97Zm.932-5.377H5.674c.082-1.603.44-2.989.932-3.971C7.21 2.118 7.784 1.906 8 1.906c.216 0 .79.212 1.394 1.42.491.982.85 2.368.932 3.97Zm1.408 1.406c-.09 1.915-.538 3.622-1.21 4.846a6.1 6.1 0 0 0 3.53-4.846h-2.32Zm2.32-1.406h-2.32c-.09-1.915-.538-3.622-1.21-4.845a6.1 6.1 0 0 1 3.53 4.845Zm-9.788 0c.09-1.915.538-3.622 1.21-4.845a6.099 6.099 0 0 0-3.53 4.845h2.32Zm-2.32 1.406a6.1 6.1 0 0 0 3.53 4.846c-.672-1.224-1.12-2.93-1.21-4.846h-2.32ZM15.5 8a7.5 7.5 0 1 0-15 0 7.5 7.5 0 0 0 15 0Z"
                          ></path>
                        </svg>
                      </div>
                      <div class="mono-number">GMT-05:00</div>
                      <div class="place">Toronto</div>
                    </div>
                  </div>
                </div>

                <template #panel="{ close }">
                  <UCommandPalette>
                    <template #empty-state>
                      <div class="flex flex-col items-center justify-center py-6 gap-3">
                        <span class="italic text-sm">Nothing here!</span>
                      </div>
                    </template>
                  </UCommandPalette>
                </template>
              </UPopover>
            </div>
          </div>
          <div class="item-box mt-4 rounded-lg">
            <div class="icon">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
                <g
                  fill="none"
                  fill-rule="evenodd"
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="1.5"
                >
                  <path
                    d="M2 6.854C2 11.02 7.04 15 8 15s6-3.98 6-8.146C14 3.621 11.314 1 8 1S2 3.62 2 6.854Z"
                  ></path>
                  <path d="M9.5 6.5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0Z"></path>
                </g>
              </svg>
            </div>
            <div class="info">
              <div class="h2">添加活动地点</div>
              <div class="h3">线下地点或虚拟链接</div>
            </div>
          </div>
          <div class="item-box mt-4 rounded-lg">
            <div class="icon">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
                <path
                  fill="currentColor"
                  fill-rule="evenodd"
                  d="M7.75 0h-.055c-1.367 0-2.47 0-3.337.117-.9.12-1.658.38-2.26.981-.602.602-.86 1.36-.981 2.26C1 4.225 1 5.328 1 6.695V8.805c0 1.368 0 2.47.117 3.337.12.9.38 1.658.981 2.26.602.602 1.36.86 2.26.982.867.116 1.97.116 3.337.116h.11c1.367 0 2.47 0 3.337-.116.9-.121 1.658-.38 2.26-.982.602-.602.86-1.36.982-2.26.116-.867.116-1.97.116-3.337V6.695c0-1.367 0-2.47-.116-3.337-.121-.9-.38-1.658-.982-2.26-.602-.602-1.36-.86-2.26-.981C10.275 0 9.172 0 7.805 0H7.75ZM3.159 2.159c.277-.277.665-.457 1.4-.556.754-.101 1.756-.103 3.191-.103 1.435 0 2.437.002 3.192.103.734.099 1.122.28 1.399.556.277.277.457.665.556 1.4.101.754.103 1.756.103 3.191v2c0 1.435-.002 2.437-.103 3.192-.099.734-.28 1.122-.556 1.399-.277.277-.665.457-1.4.556-.754.101-1.756.103-3.191.103-1.435 0-2.437-.002-3.192-.103-.734-.099-1.122-.28-1.399-.556-.277-.277-.457-.665-.556-1.4-.101-.754-.103-1.756-.103-3.191v-2c0-1.435.002-2.437.103-3.192.099-.734.28-1.122.556-1.399ZM4.5 7.25a.75.75 0 0 1 .75-.75h2a.75.75 0 0 1 0 1.5h-2a.75.75 0 0 1-.75-.75Zm0 3.5a.75.75 0 0 1 .75-.75h4a.75.75 0 0 1 0 1.5h-4a.75.75 0 0 1-.75-.75Z"
                ></path>
              </svg>
            </div>
            <div class="info">
              <div class="h2">添加信息</div>
            </div>
          </div>
          <div class="h4-title">活动选项</div>

          <div class="options-card rounded-lg">
            <div class="item-box">
              <div class="icon">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
                  <path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M3.204 1.25C1.44 1.25.251 2.938.251 4.692V6.146c-.001.068-.001.163.007.247a.96.96 0 0 0 .162.466c.142.205.348.298.411.327l.005.002c.083.038.185.076.277.11l.016.007c.177.066.394.309.394.696 0 .387-.217.63-.394.696l-.017.007c-.091.034-.193.072-.276.11l-.005.002c-.063.029-.269.122-.411.327a.96.96 0 0 0-.162.465c-.008.084-.008.18-.008.247v1.453c0 1.755 1.188 3.443 2.954 3.443h9.592c1.766 0 2.954-1.688 2.954-3.443V9.854c0-.068 0-.163-.008-.247a.96.96 0 0 0-.162-.465c-.142-.205-.348-.298-.411-.327l-.005-.003a4.503 4.503 0 0 0-.276-.11l-.017-.006c-.177-.066-.394-.309-.394-.696 0-.387.217-.63.394-.696l.017-.007c.091-.034.193-.072.276-.11l.005-.002a.993.993 0 0 0 .411-.327.96.96 0 0 0 .162-.466c.008-.084.008-.179.008-.247V4.693c0-1.755-1.19-3.443-2.954-3.443H3.204ZM1.751 4.693c0-1.221.784-1.943 1.453-1.943H9.25v3.008a.75.75 0 0 0 1.5 0V2.75h2.046c.669 0 1.453.722 1.453 1.943v1.244c-.788.344-1.272 1.178-1.272 2.063 0 .885.484 1.72 1.273 2.063v1.244c0 1.221-.784 1.943-1.454 1.943H10.75v-2.492a.75.75 0 0 0-1.5 0v2.492H3.204c-.67 0-1.454-.722-1.454-1.943v-1.244C2.54 9.719 3.023 8.885 3.023 8c0-.885-.484-1.72-1.273-2.063V4.693Z"
                  ></path>
                </svg>
              </div>
              <div class="info flex-1">
                <div class="h2">门票</div>
              </div>
              <div class="right-flex">
                <div class="value">免费</div>
                <button
                  aria-label="编辑"
                  class="lux-menu-trigger-wrapper btn luma-button flex-center small secondary naked edit-button icon-only-compact"
                  type="button"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    stroke="currentColor"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                  >
                    <path
                      d="M17 3a2.828 2.828 0 1 1 4 4L7.5 20.5 2 22l1.5-5.5L17 3z"
                    ></path>
                  </svg>
                </button>
              </div>
            </div>
            <div class="item-box">
              <div class="icon">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
                  <path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M7.75.25C5.336.25 3.5 2.086 3.5 4.5c0 1.225.474 2.007.9 2.575.09.12.165.216.23.298.102.13.18.228.255.345.101.158.115.233.115.282 0 .34-.126.536-.392.728-.3.217-.708.375-1.25.585l-.13.05c-.55.215-1.233.49-1.767.954C.88 10.821.5 11.524.5 12.5c0 .752.341 1.354.85 1.799.488.427 1.133.717 1.81.92 1.354.406 3.065.531 4.59.531a.75.75 0 0 0 0-1.5c-1.475 0-3.014-.125-4.16-.468-.573-.173-.99-.383-1.252-.612-.242-.211-.338-.422-.338-.67 0-.524.18-.821.446-1.052.309-.269.751-.463 1.326-.687l.159-.061c.493-.19 1.087-.418 1.555-.756C6.064 9.527 6.5 8.91 6.5 8c0-.451-.174-.813-.353-1.093-.112-.173-.265-.37-.397-.537a12.843 12.843 0 0 1-.15-.195c-.324-.432-.6-.9-.6-1.675 0-1.586 1.164-2.75 2.75-2.75S10.5 2.914 10.5 4.5c0 .672-.208 1.11-.463 1.484a.75.75 0 1 0 1.24.843A3.962 3.962 0 0 0 12 4.5C12 2.086 10.164.25 7.75.25Zm7.561 9.247a.75.75 0 0 0-1.122-.994l-2.962 3.34-.896-1.096a.75.75 0 0 0-1.161.95l1.454 1.778a.75.75 0 0 0 1.142.023l3.545-4Z"
                  ></path>
                </svg>
              </div>
              <div class="info flex-1">
                <div class="h2">需要批准</div>
              </div>
              <div class="right-flex">
                <UToggle v-model="selectedToggle" />
              </div>
            </div>
            <div class="item-box">
              <div class="icon">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
                  <path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M8 15.5a.75.75 0 0 0 .75-.75V10.5h.041c.872 0 1.609 0 2.159-.08.55-.08 1.195-.277 1.5-.928.305-.65.043-1.273-.248-1.746-.29-.474-.762-1.04-1.32-1.71l-.04-.047-.422-.507-.033-.04c-.399-.478-.748-.897-1.072-1.19-.348-.314-.769-.578-1.315-.578-.546 0-.966.264-1.315.578-.324.293-.673.712-1.071 1.19l-.034.04-.422.507-.04.047c-.557.67-1.03 1.236-1.32 1.71-.29.473-.552 1.096-.248 1.746.305.651.95.848 1.5.928.55.08 1.288.08 2.16.08h.04v4.25c0 .414.336.75.75.75ZM4.921 8.85c.046.022.145.057.345.086C5.695 8.998 6.321 9 7.27 9h1.46c.95 0 1.576-.002 2.004-.064.2-.03.3-.064.345-.086a1.25 1.25 0 0 0-.155-.32c-.227-.369-.626-.851-1.234-1.58l-.422-.507c-.442-.53-.723-.865-.958-1.077-.213-.193-.29-.192-.308-.192h-.003c-.02 0-.096 0-.308.192-.235.212-.516.546-.958 1.077l-.423.507c-.608.729-1.007 1.211-1.234 1.58-.106.173-.143.271-.155.32ZM14 2a.75.75 0 0 0 0-1.5H2A.75.75 0 1 0 2 2h12Z"
                  ></path>
                </svg>
              </div>
              <div class="info flex-1">
                <div class="h2">人数</div>
              </div>
              <div class="right-flex">
                <div class="value">无限制</div>
                <button
                  aria-label="编辑"
                  class="lux-menu-trigger-wrapper btn luma-button flex-center small secondary naked edit-button icon-only-compact"
                  type="button"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    stroke="currentColor"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                  >
                    <path
                      d="M17 3a2.828 2.828 0 1 1 4 4L7.5 20.5 2 22l1.5-5.5L17 3z"
                    ></path>
                  </svg>
                </button>
              </div>
            </div>
          </div>

          <UButton block class="mt-4">创建活动</UButton>
        </div>
      </div>
    </div>
  </main>
</template>
<script setup lang="ts">
import dayjs from "dayjs";

const selectedToggle = ref(false);

// 开始时间
const startDate = ref(new Date());
const StartTimePeople = [];
const Startimes = Array.from({ length: 48 }, (_, i) => {
  let hour = Math.floor(i / 2);
  let minute = i % 2 === 0 ? "00" : "30";
  return StartTimePeople.push(`${hour.toString().padStart(2, "0")}:${minute}`);
});
const StartTimeSelected = ref(StartTimePeople[0]);

// 结束时间
const endDate = ref(new Date());
const EndTimePeople = [];
const Endtimes = Array.from({ length: 48 }, (_, i) => {
  let hour = Math.floor(i / 2);
  let minute = i % 2 === 0 ? "00" : "30";
  return EndTimePeople.push(`${hour.toString().padStart(2, "0")}:${minute}`);
});
const EndTimeSelected = ref(EndTimePeople[0]);
</script>
<style scoped lang="less">
input[type="time"]::-webkit-calendar-picker-indicator {
  display: none;
}

.page-container {
  min-height: auto;
  position: relative;
  background: transparent;
  .event-page-left {
    width: 330px;
    border-radius: 10px;
    overflow: hidden;
  }
}
.event-page-content-wrapper {
  display: flex;
  -webkit-box-align: flex-start;
  align-items: flex-start;
  gap: 2rem;
  padding: 1rem;
  --gap: 1.5rem;
}
.zm-container {
  max-width: 960px;
  margin: 0 auto;
}

.photo-container {
  width: 330px;
  position: relative;
  cursor: pointer;
  .img-aspect-ratio {
    border-radius: 10px;
    overflow: hidden;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  &:hover {
    .button-icon {
      background-color: #a63450;
    }
  }
  .button-icon {
    position: absolute;
    border-radius: 100%;
    bottom: 0.5rem;
    right: 0.5rem;
    background: #430003;
    color: #fff;
    border: 2px solid #fff;
    width: 2.25rem;
    height: 2.25rem;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    svg {
      width: 1rem;
      height: 1rem;
    }
  }
}

.create-theme-button {
  width: 100%;
  margin-top: 20px;
  padding: 8px 12px;
  border-radius: 15px;
  border: 1px solid rgb(235, 236, 237);
  background-color: rgb(235, 236, 237);
  display: flex;
  align-items: center;
  flex: 1 1;
  grid-gap: 10px;
  transition: all 0.3s ease;
  &:hover {
    background-color: rgb(224, 224, 225);
  }
  img {
    width: 3rem;
  }
  .texts {
    width: 100%;
    text-align: left;
    .h2 {
      font-size: 0.75rem;
      color: rgba(19, 21, 23, 0.36);
    }
    .h3 {
    }
  }
  .icon {
    width: 1.5rem;
    height: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    svg {
      stroke: #777;
    }
  }
}

.time-picker {
  display: flex;
  gap: 6px;

  .box1 {
    background: rgba(19, 21, 23, 0.04);
    border-radius: 0.5rem;
  }
  .timeline {
    position: absolute;
    top: 1.75rem;
    bottom: 1.75rem;
    left: 1.2875rem;
    border-left: 1.5px dashed rgba(19, 21, 23, 0.2);
  }
  .flex-baseline {
    padding: 2px;
    padding-left: 0.75rem;
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    gap: 2px;
    .time-input,
    .date-input {
      max-width: 11rem;
      padding: 4px;
      background-color: rgba(19, 21, 23, 0.04);
    }
    .time-input {
      width: 7rem;
    }
    input {
      min-width: 0;
      display: flex;
      background: transparent;
      font-size: 1rem;
      outline: none;
      color: rgb(19, 21, 23);
      width: 100%;
      border: 0 solid transparent;
      border-radius: 0.25rem;
      text-align: left;
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;
      -webkit-align-items: center;
      -webkit-box-align: center;
      -ms-flex-align: center;
      align-items: center;
    }
  }
}

.start-row {
  .dot {
    background-color: rgba(19, 21, 23, 0.2);
    margin: 0 0.375rem 0 0.25rem;
    width: 0.625rem;
    height: 0.625rem;
    border-radius: 100%;
    -webkit-flex-shrink: 0;
    -ms-flex-negative: 0;
    flex-shrink: 0;
  }
}
.end-row {
  .dot {
    border: 1.5px solid rgba(19, 21, 23, 0.2);
    margin: 0 0.375rem 0 0.25rem;
    width: 0.625rem;
    height: 0.625rem;
    border-radius: 100%;
    -webkit-flex-shrink: 0;
    -ms-flex-negative: 0;
    flex-shrink: 0;
  }
}
.tz-input {
  background: rgba(19, 21, 23, 0.04);
  position: relative;
  border-radius: 0.5rem;
  backdrop-filter: blur(16px);
  .text-secondary-alpha {
    display: flex;
    -webkit-flex-direction: column;
    -ms-flex-direction: column;
    flex-direction: column;
    height: 100%;
    padding: 0.5rem 0.625rem;
    width: 140px;
  }
  .icon {
    margin-bottom: 0.3125rem;
    svg {
      width: 1rem;
      height: 1rem;
    }
  }
  .mono-number {
    font-size: 0.875rem;
    line-height: 1.3;
    font-weight: 500;
  }
  .place {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-size: 0.8125rem;
  }
}
.h4-title {
  font-size: 14px;
  margin: 10px 0 5px;
}
.options-card {
  overflow: hidden;
  backdrop-filter: blur(20px);
  .item-box {
    border-top: 1px #e9e9e9 solid;
    &:first-child {
      border-top: 0;
    }
  }
}
.item-box {
  background: rgba(19, 21, 23, 0.04);
  position: relative;
  flex: 1 1;
  backdrop-filter: blur(16px);
  display: flex;

  padding: 10px;
  grid-gap: 10px;
  cursor: pointer;
  .icon {
    margin-top: 4px;
    svg {
      width: 1rem;
      height: 1rem;
    }
  }
  .info {
    .h2 {
    }
    .h3 {
    }
  }
  .right-flex {
    display: flex;
    grid-gap: 5px;
    svg {
      width: 1rem;
      height: 1rem;
    }
  }
}
</style>
