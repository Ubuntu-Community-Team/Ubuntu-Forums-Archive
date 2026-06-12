---
title: "bootup problem due to cd"
date: 2006-05-09
forum: Hardware &amp; Laptops
---

### Post by anandam on 2006-05-09
Hi everybody,

Whenever I try to bootup using rescue mode, the screen gets stuck at following thing.
"request sense failure : 0x7f {IllegalLength Indication EndOfMedia AbortedCommand MediaChangeRequested LastFailedSense=0x07}"

Also, when I finally I get into it after try for many times, I can not open the cd-rom.It says 
"special device /dev/hdc does not exist"

Please, somebody help me.

---

### Post by anandam on 2006-05-11
Is there nobody who can help me..?

---

### Post by Sef on 2006-05-11
Why are you booting up into rescue mode?

---

### Post by anandam on 2006-05-11
Hi Sef,

I am booting from recovery mood since I was getting stuck at normal booting.

---

### Post by Sef on 2006-05-11
Try this from the Terminal (Applications > Accessories > Terminal):

sudo apt-get update

sudo apt-get install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

Let's see if this will install your programs that you are missing.

---

### Post by anandam on 2006-05-11
Sef

I don't have internet on the concerned machine. I can download deb files from other machine  and install them. So what should I do?

---

