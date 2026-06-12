---
title: "A new LCD Monitor installed"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by wshamroukh on 2006-03-27
Hi all

i changed the monitor on my ubuntu box to Proview LCD monitor.. but the ubuntu could not view anything on the monitor.. what should i do to configure my ubuntu in order to be able to view through this monitor?

thanx in advance

---

### Post by bfbay315 on 2006-03-27
you probaly need to changed the refresh rate in your xserver settings.

Find the refresh rate in your monitor documentation and edit /etc/X11/xorg.conf 
with the proper refresh rate in the monitor section of xorg.conf

there are several posts that walk you through this so I wont...but I believe that the refresh rate is your problem..


brian

---

