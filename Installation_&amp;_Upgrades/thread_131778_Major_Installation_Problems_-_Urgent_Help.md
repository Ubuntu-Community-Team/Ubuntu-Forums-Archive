---
title: "Major Installation Problems - Urgent Help"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by DCX on 2006-02-17
Well I finally received my Ubuntu CD in the mail and went to put it on my laptop (Toshiba Qosmio F10) 

First off, I believe my partioning attempts deleted my Windows XP Media Center Edition completely:cry: As it no longer shows up in the list of bootable OS systems. I don't suppose I can retreave the info from it can I?

Anyways on to Linux... I got all of the way up to the part were you eject the disk and restart. It runs the ubunto logo comes up on the black background and then that goes away and text pops up saying it is configuring things and OK keeps coming up except for a failure in name resolution. Then it asks me for my username and password, I put them in and it shows that there is no warranty and that it is free software and what not...

dale@DCXUbuntu:~$ then comes up. I try to type things into but it doesn't do anything at all! 

This is where I am stuck, please help. Also, is all of the data from my Windows system (files and what not) gone forever at this point?

Thank you:cry:

---

### Post by linbetwin on 2006-02-17
Try typing **startx** and press ENTER.

---

### Post by DCX on 2006-02-17
Alright, tried that. It says "startx: command not found":(

---

### Post by marisy2k on 2006-02-17
What type of graphics card do you use?

---

### Post by DCX on 2006-02-17
nVidia GeForce FX Go5700

---

### Post by marisy2k on 2006-02-17
Once you are in the prompt open up /etc/X11/xorg.conf:

sudo nano -w /etc/X11/xorg.conf

scroll to where yor video driver is listed and post what your driver's value is.
I think it should be nvidia.

I use a ATI Radeon card and it gave me display problem when it was ati for the driver.
All I did was change it to vesa and it worked. I am not sure if you changing to vesa
from whatever driver is there for you will fix it.

---

