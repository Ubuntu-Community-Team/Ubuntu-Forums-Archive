---
title: "Swapped lines of pixels"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by -Phi- on 2007-05-29
I have a Toshiba Lifebook s7110 that for the most part runs Xubuntu Feisty just dandy. However, every once and a while when I boot or resume from standby, two lines of pixels on my screen swap. I've attached a screenshot where you can see the line of pixels on the right side of the screen, and the location they're taken from on the left. Sometimes the lefthand side has a misplaced row of pixels too.

I'd suspect a hardware issue, but the cursor can run over the line without looking weird. Rebooting usually solves the issue temporarily.

The graphics card is an intel 950 and I have 915resolution installed.

Any suggestions?

- Phi

---

### Post by acamargob on 2008-07-21
I have a similar problem. Im using a HP dv2125la, but the graphics card is the same one... perhaps it has something to do with 915resolution being installed

---

### Post by -Phi- on 2008-07-21
To follow up on my post, this problem slowly became more rare as the Intel driver was updated, and disappeared entirely when I upgraded to Hardy. 

I concluded that my problem was [Bug #91966]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/91966"), which they have a fix released for. Perhaps you can find some help in the report? See the related [Bug #133118]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133118") too.

Cheers and good luck,
- Phi

---

