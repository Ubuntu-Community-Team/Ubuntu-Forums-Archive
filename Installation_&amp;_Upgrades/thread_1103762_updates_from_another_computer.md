---
title: "updates from another computer"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by kimikrishna on 2009-03-23
i have a 128 kBps net speed so that i cant update my ubuntu..... updates are 200 mb pending still..... whereas my friend has 2 mb ps net speed ..... if he downloads and installs the updates , how do i copy them from his computer and update mine ??

i use 8.10 32 bit on a 64 bit processor...

---

### Post by cariboo on 2009-03-23
You could use aptoncd, it is in the repositories.

All the downloaded packages are archived in /var/cache/apt/archives.

Jim

---

### Post by kimikrishna on 2009-03-23
i have installed apt on cd..

then, what to do ?? 

 i mean, do i need to install this in his computer too ??

---

### Post by kimikrishna on 2009-03-25
i will copy updates from my friend's computer in to CD..

what tto do next ?? ::(

---

### Post by Anthon on 2009-03-25
sudo dpkg --install *.deb
would install of the packages

---

