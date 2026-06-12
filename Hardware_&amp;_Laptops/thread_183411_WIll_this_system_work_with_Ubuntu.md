---
title: "WIll this system work with Ubuntu?"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by pkulak on 2006-05-28
I'm going to swap out my motherboard, processor and video card. Here's what I'm thinking:

ABIT KN8 with the  AMD Athlon 64 X2 3800+ and a GForce 6600 video card.

Does that bring up any warning bells? Would you make any changes? Thanks!

---

### Post by khightower on 2006-05-28
This system looks like it will install fine. After install be sure to install the Nvidia drivers to get better RES and proformace out of your video card

---

### Post by Sutekh on 2006-05-28
Sounds just like my setup.

MSI K8N, 3800 X2, 6600 GT.

You will want a SMP (symmetric multi-processing) kernel.  If you install the 32bit Ubuntu, you can get the **linux-k7-smp** package that has a SMP kernel for your dual core.  

As for the NVIDIA card, you might want to check out this thread.

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

 - Method 1 is by far the easiest method, and will install the Ubuntu repository NVIDIA drivers (v7667)

 - Method 2 is a little harder and can be used to install any version of the proprietry NVIDIA drivers.



You'll have plenty of time to discover all this.  Bottom line; your hardware should be fine!

---

### Post by pkulak on 2006-05-28
Just what I wanted to hear. I'm going to have to look into that SMP thing. I figured it would just throw different threads at different cores no matter what kernal you were running.

---

