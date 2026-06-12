---
title: "Cannot get widescreen to work in Feisty"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by webmaren on 2007-06-04
No matter how many times I rewrite xorg.conf I can't get my display to go back to 1280x800. It's locked on 1024x768. Worked until about 1 hour ago. Interestingly enough, it doesn't go to 4:3 until i log in, up to that point its on the right res.

> sam@webmaren:~$ sudo ddcprobe
Password:
vbe: VESA 2.0 detected.
oem: ATI RV370
memory: 16384kb
mode: 800x600x16
mode: 1024x768x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 132x25 (text)
mode: 132x43 (text)
edid: @
edidfail


Using an X2GEN MW15A, ATI RADEON X550.

---

### Post by webmaren on 2007-06-05
Never mind, I got it fixed after two hours.

---

### Post by grogling on 2007-06-06
care to explain how, i'm in the same position.

---

