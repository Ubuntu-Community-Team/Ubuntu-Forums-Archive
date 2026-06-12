---
title: "Laptop Screen Resolution"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by ahmedzafar on 2007-05-30
I have a Fujitsu-Siemens E8020D (Intel Chipset) Laptop. The VGA Card used is Intel 915GM/GMS,910GML Express chipset. My current resolution is 1024X768, and it can go up to 1600X1200. But when i change it to 1600X1200, the laptop screen shows only part of the top-left of the desktop, to view the bottom-left, I have to scroll down with my mouse. Why can't i see the whole screen? My Friend also has the same laptop and his current resolution is 1600X1200. Please help. I am using the latest VGA drivers from Intel website.

---

### Post by Tilo on 2007-05-31
what you are seeing is a virtual desktop of 1600x1200 with a physical window of 1024X768 pixels?

Please post your /etc/X11/xorg.conf file.. there must be something messed up in the "Screen" section.

   Tilo

---

