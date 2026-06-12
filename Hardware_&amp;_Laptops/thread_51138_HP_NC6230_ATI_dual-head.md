---
title: "HP NC6230 ATI dual-head"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by Crimson Tide on 2005-07-22
I have NC6230 installed with the HP Ubuntu.  Internal LCD works good.  Also have a docking station and DVI output to second LCD monitor.  Have ATI x300 w/ 64MB RAM.

How do I activate this monitor to give me either expanded screen or dual desktops?

In Fedora Core 4 I find this option easily.  Can't find it on Ubuntu....

Thanks!

---

### Post by phen on 2005-09-27
i dont like unanswered threads, so allthough i think you have found the answer elsewhere until now, i will tell you what i know about it:
you have to edit the file /etc/X11/xorg.conf. there are many explanations in this forum how to do it. maybe you should search for "howto dual head". basically, you have to add second device, screen and monitor sections. you have to edit the server layout section as well.

i would love to hear from you how the docking station is supported from linux. i want to buy one for myself, and i've heard rumours that it will work. but i am happy about every new detail :)

cheers

---

