---
title: "login issue"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by LouisvilleLIP on 2007-07-10
My laptop screen blinks, then exits back to the login screen.  After about 5 attempts, it lets me login with the correct resolution.  This didn't occur until I followed these directions:

> Have you tried using the "intel" driver instead of i810?

To do so install xserver-xorg-video-intel from synaptic / apt-get and then run:
Code:

sudo dpkg-reconfigure xserver-xorg -phigh

That command should ask you for the driver you want to use ( choose "intel" ) and the resolution you want. Once that is done restart X ( close all open applications and press ctrl+alt+backspace ) and hopefully you will be brought to a full resolution login screen 


How can I get this to let me log in on the first try?

---

### Post by LouisvilleLIP on 2007-07-11
bump

---

### Post by LouisvilleLIP on 2007-07-11
bump

---

