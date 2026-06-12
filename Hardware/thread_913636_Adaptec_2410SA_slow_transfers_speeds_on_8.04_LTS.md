---
title: "Adaptec 2410SA slow transfers speeds on 8.04 LTS"
date: 2008-09-07
forum: Hardware
---

### Post by evolutionxtinct on 2008-09-07
I'm currently running:

Adaptec 2410SA Controller
4x 500GB Seagate RAID Edition NS Drives

on:

Ubuntu 8.04 LTS
Kernel: 2.6.24-19-server

for some reason, i am getting very slow transfer speeds from:

from: /media/RAID/database
to: /media/RAID/backup

I noticed when doing lspci I get this for the adaptec card:

RAID bus controller: Adaptec AAC-RAID (rev 01)

Does anyone know how to get better performance? I'm currently getting 10MBps seems pretty weak....

Thanks! :confused:

---

### Post by cariboo on 2008-09-07
HAve a look at his page, it may help:

[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1296399,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1296399,00.html)

Jim

---

### Post by evolutionxtinct on 2008-09-08
My main goal is to try enhancing the performance, installing ASM was another thing I was going to do after I got this problem reolved. But being tired of looking for other links I did go thru the ASM install :) Only problem i have now is getting it to work when my box is connected to the domain. And yes i did use <DOMAIN>\administrator and a account thats linked in the AD and it still didn't work!! But i'll face that problem once i get resolution of the performance :) So any other suggestions :lolflag:

Thanks! :confused:

---

