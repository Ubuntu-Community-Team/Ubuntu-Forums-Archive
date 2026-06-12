---
title: "Keypad freezes at startup so I can't scroll to start Windows"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by ElliottJB on 2009-10-10
I'm totally new to Ubuntu. Bought a magazine with Ubuntu 9.04 disk and decided to try it out. My hard drive is not partitioned. When installing, I chose the option of letting Ubuntu partition automatically, not manually. On first re-boot, I discovered the arrow keys would not work so I couldn't choose which operating system to open. Ubuntu opened by itself. Then I let Ubuntu install all the updates. The next time I re-booted, the arrow keys would work. But ever since, the keys are frozen and I can't choose to go into XP. Please help me solve this with the most simple directions possible, as I don't know a thing about Ubuntu or Linux and I must, until I learn, get into XP. Thanks.

---

### Post by stlsaint on 2009-10-10
i would recommend that you either re-install ubuntu or remove it and install ubuntu using wubi. wubi will allow you to test ubuntu without partitioning your hdd and if you want to remove a wubi install you can simply remove it under add/remove programs in windows! also to test ubuntu you can just boot to the livecd and test from there without installing anything. 

Now to remove ubuntu you need to boot into the live cd and delete the partitions that ubuntu made for itself...you cannot do this under windows as windows doesnt recognize the ubunut filesystem! (ext2,ext3.etc etc)

---

### Post by presence1960 on 2009-10-11
do you have an USB keyboard? If so you need to go into BIOS and enable USB keyboard or Legacy USB.

---

