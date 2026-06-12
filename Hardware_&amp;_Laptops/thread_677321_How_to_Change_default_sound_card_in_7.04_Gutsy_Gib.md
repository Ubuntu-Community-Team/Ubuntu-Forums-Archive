---
title: "How to Change default sound card in 7.04 Gutsy Gibbon"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by roadrash on 2008-01-24
I tried everything but this worked for me on Linux Mint Daryna which uses Ubuntu Gutsy.  It should also work in Kubuntu.

open a shell and type **sudo apt-get install linux-ubuntu-modules-2.6.22-14-386**

This knocks out the nvidia driver if you have it installed so do it before installing it. If you have already installed it & knock it out then you need to reset the driver to "nv" by entering **sudo nano /etc/X11/xorg.conf** & then scrolling down the file looking for any sections called "Device" & changing the "Driver" from "nvidia" to back to "nv". Once done save the file & type "startx" to get the desktop. I don't know what to do about ATI & other Cards.

---

