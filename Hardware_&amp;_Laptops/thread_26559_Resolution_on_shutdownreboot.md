---
title: "Resolution on shutdown/reboot"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by haaglin on 2005-04-13
Hi. 

I have changed the resolution in my menu.lst file to have 1024x760 (vga=792), this works fine during boot, and looks very good too, but when i restart my computer, or shutdown, it all get screwed up. I have a nVidia GeForce FX5600 256MB video card, so i know it can handle it. I have done the same thing on two other computers, but only mine has that problem. I have installed the nVidia driver. Has anybody seen this problem before and has a solution?  Thanks in advance.

---

### Post by erkki70 on 2005-04-13
Hi,
Maybe try to run ```
sudo update-grub
```after making your changes in /boot/grub/menu.lst config file?

Hope this helps.

Cheers,
Erkki

---

### Post by haaglin on 2005-04-13
Have done that already. :?

---

### Post by haaglin on 2005-04-13
I discovered that during Shutdown/reboot, the resolution is 640x350 @70Hz, But during boot, it is 1024x760. And in X, i'm running at 1280x1024 @ 60Hz. So why does it show it at 640x350 and 70hz during Shutdown/reboot, but not during boot?

---

### Post by haaglin on 2005-04-13
anyone?

---

### Post by nad on 2005-04-13
Your change, vga=792, needs to be put on the kopt line in order for it to be persistent. Otherwise, update-grub will not keep your instructions.

Dan M

---

### Post by haaglin on 2005-04-13
I know, did that too.

---

### Post by haaglin on 2005-04-14
Bump!

---

### Post by odix on 2005-04-14
try changing it to vga=791 (1024x768x16) or vga=794 (1280x1024x16), sometimes framebuffer-console don't like 24bit modes

regards odiX

---

### Post by haaglin on 2005-04-14
Thank You! changing it to 794 did it.

---

