---
title: "Play 3D games in Ubuntu 7.10"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by tommyhakinen on 2008-03-19
Hi,

I am new to Ubuntu. Just installed Ubuntu 7.10 a few days ago.

I am having a problem with graphics card and drivers. I would like to know how to let my laptop to be able to play 3D games such as Wolfenstein: Enemy Territory. What do i need to install before i can play.

I am using Intel integrated graphics card.
here are the informations i got from the hardware information.
Vendor : Intel Corporation
Device : Mobile 915GM/GMS/910GML Express Graphics Controller

Thanks in advance for your help

Best Regards,

Tommy

---

### Post by InvIsiBlekID on 2008-03-21
I would install 915resolution:
```
sudo apt-get install 915resolution
```
I do not have alot of experience with intel graphics cards, but that should fetch the driver for you.  After that just restart your xserver or reboot your machine and you should have 3d acceleration.

---

### Post by tommyhakinen on 2008-03-30
Yes, I have installed 915resolution, but how do I know that I am having 3D acceleration?
Thank you

---

