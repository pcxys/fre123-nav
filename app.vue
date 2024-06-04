<template>
	<NuxtLayout>
		<NuxtPage />
	</NuxtLayout>
</template>

<script setup lang="ts">
import { getConfigItem, CONFIG_KEY_SEO } from './stores/config'

const seoInfo = getConfigItem(CONFIG_KEY_SEO)
console.log(seoInfo)
// 初始化 SEO_TITLE 模板和主题
useHead({
	titleTemplate: (s) => {
		return s ? `${s} - ${seoInfo['title']}` : `${seoInfo['title']}`
	},
	link: [
		{
			rel: 'icon',
			type: 'image/x-icon',
			href: seoInfo['icon'],
		},
	],
	meta: [
		{
			name: 'keywords',
			content: seoInfo['keywords'],
		},
		{
			name: 'description',
			content: seoInfo['description'],
		},
	],
	bodyAttrs: {
		class: 'bg-base',
	},
}),
useHead({
	script: [
		{
			src: `https://tj.liaofei.org/script.js`,
			defer: true,
			mode: 'client',
			'data-website-id': '3a5a502b-1315-4b74-8cb7-b14bfe2e385a',
		},
	],
})
</script>
