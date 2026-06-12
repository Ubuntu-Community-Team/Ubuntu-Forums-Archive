---
title: "just a small question"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Duero on 2009-01-30
to Install ubunto I need to install it on another partition than windows right ?? I wanna be able to pick Windows or Unbuntu when I start my computer but when I installed it on the same drive as Windows, Windows stoped working how shall I do. I did a search here but did not find anything that gave ma an answer.

---

### Post by taurus on 2009-01-30
You mean you won't be able to boot windows anymore?  While you are in Ubuntu, open a terminal and see if your windows is still there (on the harddrive).

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by Duero on 2009-01-31
> **taurus said:**
> You mean you won't be able to boot windows anymore?  While you are in Ubuntu, open a terminal and see if your windows is still there (on the harddrive).

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.


I Mean I wanna be able to have both windows and ubuntu installed on my computer so when I start my computer I can pick windows or ubuntu so I wonder how do I do that with out losing windows as I die last time.

---

### Post by mhh91 on 2009-01-31
you'll keep the windows on the "C" drive,and install ubuntu on a logical drive,and GRUB will let you choose between them :)

---

### Post by Duero on 2009-01-31
> **mhh91 said:**
> you'll keep the windows on the "C" drive,and install ubuntu on a logical drive,and GRUB will let you choose between them :)

ahh so I like install Ubuntu on like D: drive ic thanks for help

---

### Post by linux_tech on 2009-01-31
Installing Ubuntu after Windows
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Duero on 2009-01-31
> **linux_tech said:**
> Installing Ubuntu after Windows
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)



Thanks allot ^^

---

