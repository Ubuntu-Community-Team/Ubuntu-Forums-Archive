---
title: "Very noisy desktop using Ubuntu 13.04 AMD64"
date: 2013-09-12
forum: Hardware
---

### Post by Coder88 on 2013-09-12
I just installed Ubuntu 13.04 amd64 yesterday to my desktop (six core, 16GB, several sata drives). It is very noisy, all fans at full out spin, very annoying considering i worked hard to make my pc quiet for writing by putting in 
(1) an ultraquiet case fan (800rpm 8.5dba)
[http://www.amazon.com/gp/product/B002IG5HFW/ref=wms_ohs_product?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B002IG5HFW/ref=wms_ohs_product?ie=UTF8&psc=1)
(2) an ultraquet cpu cooler
[http://www.amazon.com/gp/product/B0093DOO34/ref=wms_ohs_product?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B0093DOO34/ref=wms_ohs_product?ie=UTF8&psc=1)
I rebooted into Windows 7 and again my pc was ultraquiet.

Why is my PC so noisy in Ubuntu but not Windows? Is there a solution to get my pc back to quiet in Ubuntu?

---

### Post by Coder88 on 2013-09-12
I wonder if the noise was from tracker-miner-fs indexing my discs/files, as i had just installed Ubuntu 13.04 to this desktop PC yesterday? Came home and booted again, now Ubuntu is quiet. I have a System Monitor window open showing processes, I am going to watch that and if the computer gets noisy I will see if I can notice if a process has moved closed to the top of the %cpu/priority list that might hint at what process is causing the noise.

---

### Post by Coder88 on 2013-09-12
(Ubuntu desktop) Running quiet now for almost an hour. :)

---

### Post by buzzingrobot on 2013-09-12
Probably was tracker busy working to index all your drives.  Believe you can configure Tracker to index only specific drives/partitions/folders.

My MacBook used to go crazy like that when I plugged in an external drive and Spotlight set off to index it.

---

### Post by Coder88 on 2013-09-14
EDIT: well this only provided a temporary fix. Noisy again, until i rebooted into Windows 7. Then I shutdown and lubed the fan on the gpu again, booted into linux, quiet again-- for now. For some reason I think ubuntu is spinning the gpu fan at a faster rate than in windows. I need to find a fix for this,. I have a solution-- duh-- i am going to buy a FANLESS, SILENT nvidia/geforce (so i can have Compiz) video card, going to order one today!
---
i just dropped the noise level on my desktop PC by about 80+%, cost me  $2, wow. It was from the graphics card (diagnosed by putting my fingertip on the hub of the GPU fan, noise dropped immediately so I knew it was the GPU/graphics card), thought I needed a new one, but i cleaned the gpu fan with canned air and then  lubricated the gpu fan with powdered graphite and machine oil (then used canned air to blow away stray graphic on the circuitry of the gpu), running VERY quiet now.  nice. :)

---

### Post by tripp98 on 2013-09-15
Did you try to install the proprietary drivers for your video card?  Have run into this with nvidia cards many times.

---

