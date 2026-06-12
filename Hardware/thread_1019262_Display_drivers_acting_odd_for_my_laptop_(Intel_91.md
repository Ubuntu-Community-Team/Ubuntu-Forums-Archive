---
title: "Display drivers acting odd for my laptop (Intel 915GM Chipset)"
date: 2008-12-22
forum: Hardware
---

### Post by powerplayground on 2008-12-22
I see a lot of glitches in the GUI whenever I have any type of fancy visual settings enabled, and when I tried loading warcraft 3, it just crashed. How would I go about fixing this problem. I've never really messed with Linux drivers before, and the specs for my machine are in my signature.

---

### Post by namdung on 2008-12-23
Your hardware may not be supporting graphics features. You might wanna add a graphics card for smooth graphics experience.

---

### Post by powerplayground on 2008-12-23
Keep in mind that this is a laptop and the card is capable of playing warcraft 3. Also it should also be able to handle the GUI fine ,but obviously it doesnt. So is there any driver I should get?

Also how would I go about finding out info about devices and drives? The system menu is pretty limited in terms of configurability. Is there some type of child lock setting enabled thats hiding the more advanced settings?

Ive found some resources on the issue, but I'm too much of a noob to know what the heck to do >.<
[https://bugs.launchpad.net/ubuntu/+source/discover1-data/+bug/35473](https://bugs.launchpad.net/ubuntu/+source/discover1-data/+bug/35473)
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

---

### Post by powerplayground on 2008-12-23
bump

It seems that I need to install the proper drivers. I found a guide on how to install the drivers, but good god I'm dumb as a rock when it comes the the terminal, and I don't know squat about executing scripts.

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/graphics-problems-with-intel-915gm-on-dell-latitude-d610-311096/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/graphics-problems-with-intel-915gm-on-dell-latitude-d610-311096/)

I double clicked the install.sh file and it said it could not locate the pkginfo file even though the file is in the same dir. >:( Any advice on how to go about installing the proper drivers?

---

