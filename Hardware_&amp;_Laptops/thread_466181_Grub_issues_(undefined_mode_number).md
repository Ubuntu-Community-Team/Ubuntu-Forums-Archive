---
title: "Grub issues (undefined mode number)"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by inoxllor on 2007-06-06
Hello,

In Ubuntu 7.04 I had some "blurry usplash" issues so I used the vga=794 option during boot to circunvent that problem. 

Everything fine until I recently upgraded to the 2.6.20-16-generic kernel: now when I use the option vga=794 (or other) it says "undefined mode number". 
So, I got back my "blurry usplash" and have no idea how to bypass this problem... :(

Any ideas how to solve this issue?

---

### Post by inoxllor on 2007-06-06
I have found a solution: 
instead of using vga=794, I used  vga=0x0318 :D

USE:  **sudo hwinfo --framebuffer**
*This way you can see what modes are available to your monitor*.

Notes: 
1) you may have to install hwinfo via **apt-get install hwinfo**.
2) if usplash appears non centered you may have to edit its resolution USE: **sudo gedit /etc/usplash.conf**
and then **sudo update-initramfs -u -k `uname -r`**

---

