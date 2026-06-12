---
title: "helpcant get  dell mini inspirion 1010 3d card to work with ubuntu 9.10"
date: 2010-08-16
forum: Hardware
---

### Post by martinlovegoodie on 2010-08-16
I have a dell inspirion mini 1010 and I cant find a way to get my graphics working. my flash player iss choppy, when I drag a window its choppy. when I scrole through  Mozilla firefox windows it's choppy.
I've been looking online and trying different commands. nothing worked.
I installed ubuntu 10.4 and updated and 9.04 and updated nothing seams to work. I just want my resolution to work.
with any version of ubuntu that I installed,
 the sound and wifi works but this sucks cause I dont get system performances.

---

### Post by Fafler on 2010-08-16
Open a terminal and type

lspci | grep VGA && cat /proc/cpuinfo | grep name

Then post the results here. Its hard to help you, when we don't know what hardware you have.

Instead of the flash player, try installing a plugin in firefox that allows you to download videos and play them in totem. [https://addons.mozilla.org/en-US/firefox/addon/3006/](https://addons.mozilla.org/en-US/firefox/addon/3006/)

---

