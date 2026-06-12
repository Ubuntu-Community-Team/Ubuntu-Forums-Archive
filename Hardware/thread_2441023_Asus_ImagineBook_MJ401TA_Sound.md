---
title: "Asus ImagineBook MJ401TA Sound"
date: 2020-04-17
forum: Hardware
---

### Post by cmulk on 2020-04-17
Just wanted to post here because I don't see it posted elsewhere.

After initial install of 18.04 on the Asus ImagineBook, Ubuntu does not recognize the sound card and only shows a "Dummy Device".

After a bunch more searching I found the solution for related sound cards that works here. Seems that kernel drivers for this card have been fixed in 5.4+ so I installed the version at [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.5.18/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.5.18/)

Also, if you don't want to manually update your kernel, I found that the Fifth Alternate Method shown at [https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/) works on the normal Ubuntu kernel version.

---

