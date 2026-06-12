---
title: "New to Ubuntu, will this work?"
date: 2015-08-10
forum: Hardware
---

### Post by Slavaderp on 2015-08-10
Hi,
I'm a Windows user who will be building a new computer soon, and I'd like to swap to Linux/Ubuntu for my OS. But first I have a question: Is there hardware that could be incompatible with Ubuntu 14.04? If so, would the following build work on Ubuntu 14.04?

CPU-i5 4590
Motherboard-ASUS Z97-E LGA 1150 Intel Z97 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard
GPU-MSI GeForce GTX 960
Hard Drive-WD BLACK SERIES WD1003FZEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive
SSD-Kingston SSDNow V300 Series SV300S37A/120G 2.5" 120GB SATA III Internal Solid State Drive
PSU-Corsair RM Series RM550
Wifi-Gigabyte WB867D-I 802.11a/b/g/n/ac PCI-Express x1 Wi-Fi Adapter 

Also, would a Razer Kraken Pro work with Ubuntu? Thanks in advance guys.

---

### Post by dino99 on 2015-08-10
you should not find issue with these hardwares, as they are already used. To get the maximal support, the latest ubuntu version is a better choice; so go for the 15.04 installation

---

### Post by oldfred on 2015-08-10
I recently built new UEFI system with Asus-AR Z97 system. I did have to change a lot of settings in UEFI. And could only use the UEFI only to get it to boot Ubuntu installer in UEFI. UEFI & CSM did not work to offer UEFI boot.

You may have some issues with the nVidia 960. Is that also the new Maxwell series like 970/980/750?
       The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

---

### Post by Slavaderp on 2015-08-10
Thanks for your help, I'll look into 15.04, but 14.04 is a LTS version so I would want to do that unless there's a good reason not to.

---

### Post by Slavaderp on 2015-08-10
Thank you for the links, and yes, the GTX 960 uses Maxwell architecture, it's basically a 980 with half the hardware at half the price.

---

### Post by oldfred on 2015-08-10
I am running 14.04 on my Asus-AR, but have an older nVidia 620 card which just works fine with open source drive.
The advantage of 15.04 is newest kernel, support software and other drivers. Not sure now what versions are in new 14.04.3.
But as in Link above you need kernel 3.19 for nouveau driver to work.  It becomes a bit more difficult to add nVidia driver and other updates with older kernel. And you generally have to add one or more ppa to get newest drivers & kernel, so not really running default 14.04 anyway.

It looks like 14.04.3 has the 15.04 kernel. It uses the hardware enablement stack which may require further updates.
[https://lists.ubuntu.com/archives/ubuntu-announce/2015-August/000200.html](https://lists.ubuntu.com/archives/ubuntu-announce/2015-August/000200.html)

---

### Post by Slavaderp on 2015-08-10
Thank you oldfred.
Sorry if this is a really stupid question, but what is the difference between Nouveau and Nvidia drivers?

---

### Post by yancek on 2015-08-10
Check the link below on nouveau.  The nouveau is an open source drive for nvidia, the nvidia drivers are created/written by nvidia which makes the graphics card.

[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

---

### Post by mastablasta on 2015-08-12
also nouveau is reverse engineered driver, so sometimes it's performance is bleh (=basic SVGA resolution, no 3D)... but depends on the chip.

---

### Post by oldfred on 2015-08-12
Some Linux users are very adamant about only using open source code. Nothing that is not open source including the binary blob that nVidia or AMD drivers are. They say they have proprietary code that they do not want competitors to see.

Others of use prefer the open source code, but will use whatever works best. 
I will pay for some software if it is a lot better. But with Linux, sales are low so not a lot of paid software available anyway. And some Linux software that is free is better than the Windows paid version. Some not so much.

---

