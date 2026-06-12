---
title: "Display offset with Nvidia TNT Riva2"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by barakori on 2005-11-30
I recently installed Ubuntu. I have a 1024x768 LCD display (Gateway FPD1500) connected using DVI to an Nvidia TNT Riva2. I don't have a VGA output on the card.

After installing Ubuntu, I only got a 640x480 resolution (small, centered). I tweaked the xorg.conf file, and got the option to switch to 1024x768. But when I do that, the display has an offset - the top 30% of the screen are at the bottom, and the rest 70% are at the top. It's like the "frame" starts at the bottom and wraps to the top. Everything still works - I can do anything (although it's a bit hard to work this way ;-)

I tried the guide in [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia), but it changed nothing. I tried both the nvidia-glx and nvidia-glx-legacy, but it's always the same. 

Could this be wrong horiz/vert frequency in xorg.conf? I couldn't find the specs of the monitor (again, FPD1500) on the Internet, and I've heard that NVidia cards are not that good at detecting their displays.

I didn't try the driver from the NVidia site. I downloaded it, but it needed to compile the kernel, and I still don't know enough to do that.

Has this happened to anyone? I'd appreciate any help.

---

