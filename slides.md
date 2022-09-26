---
theme: seriph
background: /cover.jpeg
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
css: unocss
title: How to Build Your Own Open Source Project
download: true
---

# How to Build Your Own Open Source Project


<!-- TODO:
- Show slide number
 -->
<p class="text-xs">Press Space or ➡ for next page</p>

<div class="pt-13 relative">
  <div class="absolute px-2 py-1 rounded cursor-pointer right-0" hover="bg-white bg-opacity-10">
    <a href="https://twitter.com/hung_dev" target="_blank">https://twitter.com/hung_dev</a>
    <br />
    <a href="https://github.com/nvh95/react-advanced-2022" target="_blank">https://github.com/nvh95/react-advanced-2022</a>

  </div>
  
</div>


<style>
  .slidev-layout.cover h1, .slidev-layout.intro h1 {
    font-size: 2.5rem;
  }
</style>

<!--
Did you enjoy React Advanced so far.
I love it
In this talk, I will
-->

---
layout: center
class: text-center
---

# 🙌 Have you contributed to any Open Source projects?

<v-click>

If you haven't, I hope you will after my talk 😝.

</v-click>


---
layout: image-right
image: /hung.jpg
---

# Hi, My name is Hung 👋

- Full-time Open Source contributor
- Creator of <a href="https://github.com/nvh95/jest-preview">Jest Preview</a>
- Core member of <a href="https://www.bestofjs.org">bestofjs.org</a>
- Ex - Lead Frontend Engineer @ Got It Inc.
- Obsession with DX
- Connect with me:
  - <carbon-logo-twitter />: <a href="https://twitter.com/hung_dev" target="_blank">@hung_dev</a>
  - <carbon-logo-github />: <a href="https://github.com/nvh95" target="_blank">@nvh95</a>
  - 🔗: <a href="https://hung.dev" target="_blank">hung.dev</a>
  - 📧: hi@hung.dev

<!--
- Jest Preview: library gives you a visual debugging experience when testing a frontend app
-bestofjs: website helps you follow the growth of javascript ecosystem
- I am on twitter.
-->

---

# Table of Contents
- What is Jest Preview and why I built it?
- What struggles do I have to overcome when building an OSS project?
- What did I receive from doing OSS?
- Some tips to build your own open source project.


---

# What is Jest Preview and why I built it?

## Problem:
<div grid="~ cols-2 gap-4">
<div class="text-sm">

<v-click>

- When you run a test, you only see the result in the terminal

</v-click>

<v-click>

- You don't know what your app looks like when the test is running

</v-click>

<v-click>

- It's very hard to debug a failed test: Very Longgg HTML

</v-click>

<v-click>


<details><summary>Have you ever tried to click on a button, but there is no button, it's just the spinner is loading?
</summary>
  <video width="320" height="240" controls autoplay muted loop>
    <source src="/problem-with-current-tests.mp4" type="video/mp4">
  </video>
  </details>
  
</v-click>

<v-click>

=> Question: If `jest` can print out the HTML, can we render it on a browser?

</v-click>

<v-click>

=> Yes. We can!!

</v-click>
</div>
  <div>
    <img src="/debug-terminal.png" width="600" class="mx-auto" />
  </div>

</div>

<!--
- if writeFE tests =>
-->

---

# What is Jest Preview and why I built it?


<img src="/jest-preview-demo.gif" width="600" class="mx-auto" />

<!--
- this is test case written with react testing library 
- user interaction is controlled by testing library user event
- Instead of using screen.debug(), we use preview.debug() to screen the actual UI of our app in a browser
- Whenever you hit Save, the browser update the new UI almost immediately
-->

---

# What is Jest Preview and why I built it?

## Benefits of Jest Preview

<div grid="~ cols-2 gap-4">
<div>
<v-click>

- Debug a failed test easier

</v-click>

<v-click>

- We can see what our app looks like, so the next testing steps are easily predictable => write test faster

</v-click>

<v-click>

- Closing the gap between unit/ integration tests and e2e tests, but still fast in execution time

</v-click>

<v-click>

=> My personal experience: I write tests 200-300% faster, thanks to jest-preview

</v-click>
</div>
<div>
  <img src="/jest-preview-demo.gif" width="600" class="mx-auto" />
</div>

</div>


---
layout: iframe
url: >-
  https://stackblitz.com/edit/jest-preview?embed=1&ctl=1&file=src%2FApp.test.tsx,README.md
---

layout: center
class: text-center


---

# What struggles do I have to overcome when building an OSS project?

<!--
Take a closer look to see what struggles I had faced when building an OSS project
-->

---

# Struggles

- It's difficult.

```js 
import styles from './styles.module.css';

<div className={styles.button}>Click me</div>
```
E.g: We might know how to use CSS Modules, but we might not need to know how CSS Modules work under the hood

<v-click>
```js
require('postcss-modules')({
  getJSON: (cssFileName, json, outputFileName) => {
    console.log(JSON.stringify(json));
  },
  generateScopedName: function (name, filename, css) {
    const stringHash = require('string-hash');
    const i = css.indexOf('.' + name);
    const line = css.substr(0, i).split(/[\\r\\n|\\n|\\r]/).length;
    const removedNewLineCharactersCss = css.replace(/(\\r\\n|\\n|\\r)/g, '');
    const hash = stringHash(removedNewLineCharactersCss).toString(36).substr(0, 5);
    return '_' + name + '_' + hash + '_' + line;
  },
})
```
</v-click>

<!--
-Not only the user of a framework/ software => need to understand it deeply

-it's like you cannot find an answer when you have a question while developing OSS


-but it's a good chance for us to learn, whenver you overcome a hard problem
-->

---
layout: image-right
image: https://source.unsplash.com/L0xOtAnv94Y/1920x1080
---

# Struggles

- It takes a lot of time

<v-click>

=> You need to manage your time well

</v-click>

<v-click>

=> Always have a plan 

(A Good Plan Today is Better than a Perfect Plan Tomorrow)

</v-click>

<!--
- especially if you have a full-time job
-->

---
layout: image-right
image: https://source.unsplash.com/Md73pphIB-U/1920x1080
---

# Struggles


- Since it's an open source project, many people will come to help you


<v-click>

- Not really. For a small open source project, you might be the only maintainer

</v-click>

<v-click>

- Sometimes you want to give up/ archive the project

</v-click>

<v-click>

=> Why do you start OSS in the first place?

</v-click>


---
layout: image-right
image: https://source.unsplash.com/-8a5eJ1-mmQ/1920x1080
---

# Struggles

<v-click>

- **Financially 💸**

</v-click>


<v-click>

- Just do it for fun

</v-click>

<v-click>

- GitHub Sponsors

</v-click>

<v-click>

- Open Collective

</v-click>

<v-click>

- Freemium model

</v-click>

<!--
- do it for fun: OK, no problem
-->

---

# What did I receive from doing open source software?


- **Knowledge. A lot of knowledge.**

<img src="/meme/knowledge.jpg" width="300" />


<v-click>

- Read open source code a lot => code reading/ debugging skills improved
- Understand how the tools you use everyday work under the hood => Better programmer



- Rabbit hole: Jest, Vite core, CRA core, Websocket, chokidar, shebang, PostCSS, Babel...

</v-click>

<!--
- know how bundler works under the hood
-how to process CSS in a modern web application under the hood
-->

---

# What did I receive from doing open source software?


- **Opportunities:**



<v-click>

- Nominated for the Most Exciting Use of Technology, React Open Source Awards, React Summit
<img src="/jest-preview-nominee.png" width="300" class="mx-auto"/>

</v-click>

<v-click>

- Jobs: Companies reach out

</v-click>

<v-click>

- Conferences/ Tech events
<!-- Insert image -->

</v-click>


---

# What did I receive from doing open source software?


**Know great developers:**

- Twitter
<div class="flex gap-1 m-b-2">
<img src="/nw1.png" />
<img src="/nw2.png" />
</div>
<div class="flex gap-1 m-b-2">
<img src="/nw3.png" />
<img src="/nw4.png" />
</div>
<img src="/nw5.png" />

<!--
have chance to chat with many great engineers, authors of OSS libraries that I used every day. 


Before doing OSS, I have never thought of one day I can discuss technical with them
-->

---

# What did I receive from doing open source software?


Know great developers:


- In-person (CityJS Singapore 2022)

<div class="flex gap-1 m-b-2">
  <img src="/network/maya.jpg" class="object-cover" width="200" />
  <img src="/network/evan.jpg" class="object-cover" width="200" />
  <img src="/network/tan.jpg" class="object-cover" width="300" />
</div>

<!--
Even better, meet in person

- Maya Shivin
- Tan Li Hau
- Evan You
-->

---

# What did I receive from doing open source software?


**Know great developers:**

- In-person (JSConf Korea 2022)
<!-- TODO: Add images -->
<div class="flex gap-1 m-b-2 h-40">
  <img src="/network/jsconf/erick.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/dwane.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/jeremy.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/chuiyoung.jpg" class="object-cover" width="100" />
  <img src="/network/jsconf/jane.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/anna.jpeg" class="object-cover" width="100" />
</div>

<div class="flex gap-1 m-b-2 h-40">
  <img src="/network/jsconf/nicolo.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/hj.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/sosun.jpg" class="object-cover" width="100" />
  <img src="/network/jsconf/anu.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/ellie.jpeg" class="object-cover" width="100" />
  <img src="/network/jsconf/sona.jpg" class="object-cover" width="100" />
</div>

<!--
You might recognize some of them
- Erick Wendel
- Jeremy Wagner
- Dwane Hemmings
- Jeong Eun Lee
- Nicolò
- Hui Jing
- Anu
- Ellie
- Sona
- Shin Young
- Sosun
-->

---

# What did I receive from doing open source software?


I received a lot of thanks:
<div class="flex gap-1 m-b-2">
  <img src="/thanks/thanks1.jpg" class="object-contain" width="300" />
  <img src="/thanks/thanks2.jpg" class="object-contain" width="200" />
  <img src="/thanks/thanks5.png" class="object-contain" width="300" />
</div>
<div class="flex gap-1 m-b-2">
  <img src="/thanks/thanks3.jpg" class="object-contain" width="250" />
  <img src="/thanks/thanks4.jpg" class="object-contain" width="250" />
  <img src="/thanks/thanks6.png" class="object-contain" width="280" />
</div>

<!--
=> Motivation for me to keep doing it . 9-5
-->

---
layout: image-right
image: https://source.unsplash.com/QUHuwyNgSA0
---

# So...


How to do that?


---
layout: center
class: text-center
---

# Some tips to build your own open source project


---

# How to choose an open source project to work on?

- Should be projects you use every day
<Tweet id="1543771988333715456" scale="0.65" />

- Should solve your own problem

<!--
- difficult to contribute to a project that you don't have context
- just pick a project that you use every day
- if you solve something, open source it. It does not need to be something big. 
- Since you spend a lot of time on a particular problem, there is a high chance that other people have the same problem
-->

---
layout: image-right
image: /simple.jpg
---

# Start simple


<v-click>

- No projects are complicated when it was created

</v-click>

<v-click>

- Start simple. Just make an MVP/ PoC first. Then improve it overtime

</v-click>

<v-click>

- It's okay if the code is not clean

</v-click>

<v-click>

- If you get lost, it's OK. That's a sign that you are going to learn a ton

</v-click>


---

# Find a maintainer


<img src="https://pbs.twimg.com/media/FVxLXjtUYAESaYE?format=jpg&name=medium" class="mx-auto" width="500"/>

<!--
- Building an OSS project is hard and stressful. 
- It would be easier to have someone to discuss technical and motivate you to continue the project.
-->

---
layout: image-right
image: /glass-broken.jpg
---

# Do not start at 1.x

- A new project is full of PoC and experiments
- 1.x means your software must be backward compatible
- Major version zero (0.y.z) is for initial development. Anything MAY change at any time. The public API SHOULD NOT be considered stable.


---

# Use your own software

- When you use it as a normal user, you know if you need to adjust or add more features to make it usable

<img src="/use-own-software.jpg" width="400" />

<!--
You start a project to solve a particular issue. 
But when you use it as a normal user, you know if it is good enough, or if you need to adjust and add more features to make it usable.

all I want is to preview the UI in Jest to Chrome 🖼. PERIOD. But the more I use it, the more features I added to make it easier to use:
• Auto reload on Save
• Process CSS, images
• Automatic mode
• Pre-configured/ codemod
-->

---

# Ask for feedback

- Your software can be subjective

<img src="https://pbs.twimg.com/media/FVxLZAkUsAAlP9L?format=jpg&name=medium" width="500"/>

<!--
- can be subjective. 
Let’s ask your friends, your colleagues and your network what project should change to be more usable. 
After a while when your project gets more attention, watch out for the Issues and Discussion tabs
-->

---

# Monitor Issues and Pull Requests

- You know your software is being used when people start to report issues and send pull requests
- Have Issue and Pull Request templates
- Reproduction is the most important one
- Use labels, milestones, GitHub Actions

<img src="/github-cover.jpeg" width="450" />

<!--
1.it's magic. how people with same problem find your project2.guide people how to category and filing efficiently
-->

---

# Learn from others

![](https://pbs.twimg.com/media/FVxLZjfUcAAcByv?format=jpg&name=900x900)

<!--
- Do not reinvent the wheel. There is much good software out there already solved your problems. Learn from them, read their source code to see how they do.
- jest preview learn from many amazing projects: Vite, CRA
-->

---
layout: iframe-right
url: https://www.jest-preview.com
---

# Write documentations

Use static site generator:
- If you prefer React: https://docusaurus.io
- If you prefer Vue: https://vitepress.vuejs.org

<!--
It’s very easier for you to use your own software. But people around the world have different and special use cases. Describe what problems your project solves, installation, usage, and also caveats they might encounter clearly in the documentation.
-->

---
layout: two-cols
---

# Share it with the world

- Twitter
- Blog Posts
- Tech events

::right::

<Tweet id="1537041278956756992" scale="0.7" />

<!--
Last but not least
-->

---
layout: center
class: text-center
---

# Last but not least


---
layout: center
class: text-center
---

# Contribute to Open Source today

I hope you will have a lot of fun and learn a ton doing open source software.


---
layout: center
class: text-center
---

# Thanks for your attention!

Q&A
<div>
<img src="/qr-jest-preview.png" width="200" class="mx-auto" />
</div>

<p class="text-xs">Try <a href="https://github.com/nvh95/jest-preview" target="_blank">Jest Preview</a> and give it a star since it's free 😝</p>

<small>Slides available (and open source) at <a href="https://reactadvanced.hung.dev/" target="_blank">https://reactadvanced.hung.dev/</a></small>
