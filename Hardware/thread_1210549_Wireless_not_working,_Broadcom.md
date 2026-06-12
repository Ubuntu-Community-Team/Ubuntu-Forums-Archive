---
title: "Wireless not working, Broadcom?"
date: 2009-07-11
forum: Hardware
---

### Post by nos879 on 2009-07-11
I am new to Ubuntu and have run into problems installing my WLAN Card. I have  Broadcom 4318 in my HP Pavillion Dv5000 Laptop. For some reason I cannot install it. I have copied the bcmwl5.inf file to the desktop and it appears in the hardware section but it will not let me activate it. When I activate it says "installing" but nothing happens.

What am I doing wrong?

I have tried using ndiswrapper but I don't know how to install it. I have the folder on my desktop and it keeps saying there is no package. I have been doing

sudo apt-get install ndiswrapper-utils

is there a different way going about installing it, since the folder ndiswraper.1.55 is on my desktop?

Any help is appreciated, my wlan card is my only source of internet so I have to keep swtiching between XP and Ubuntu.

---

### Post by mikewhatever on 2009-07-11
I'd suggest going the easy way and installing a GUI front end:

**sudo apt-get install ndisgtk**

Ndiswrapper is in the repositories, so what's that folder on your desktop?

---

### Post by Kevide on 2009-07-11
Have you made sure that "Proprietary Drivers for Devices (restricted)" has been enabled in System|Administration|Software Sources under the "Ubuntu Software tab? Or "Unsuported updates (jaunty-backports" under the updates tab?

That's how I enabled my broadcom card.

---

