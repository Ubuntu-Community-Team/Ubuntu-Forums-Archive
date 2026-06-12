---
title: "No screens found upon install/upgrade 8.10"
date: 2009-01-24
forum: Hardware
---

### Post by sc_dan2002 on 2009-01-24
Hello,

Recently I installed ubuntu 8.04 on my computer (clevo d9c).  I was having all kind of problems getting the wireless card to work with it (5300 agn) and found a post that said 8.10 supported this card out of the box.

So I did an upgrade to 8.10 (oh btw, wireless card does work with 8.10, but I have to sign into a wifi point with username and password to use internet, so apt-get is out of the question).  Upon booting I now get a terminal session, and upon running startx I get the error:

(ee) Screens found but none with a usable configuration.

Fatal server error:
no screens found 
giving up

xinit:  Connection refused )erno 111): unable to connect to X server
xinit:  No such process (erno 3):  Server error



With that, I attempted to use my xorg.conf from 8.04 (as the one with 8.10 was very bleak, and had almost no configuration) to no avail.

I have attempted dpkg-reconfigure xserver-xorg, but that only gives me the 8.10 xorg.conf with hardly any configuration.

I have attempted xfix, but that has no effect.

Could anyone shed any light into this (I have been searching this forum and google for 4 days now trying to get a fix, but have found nothing useful)

---

### Post by sc_dan2002 on 2009-01-24
Anyone?

---

### Post by sc_dan2002 on 2009-01-25
Anyone have any suggestions as to where I can go to find out about this?  Is anyone out there?

---

### Post by jude347 on 2009-01-25
Look over the release notes for 8.10-  There is an issue with the Nvidia drivers in this version which worked previosly in 8.04  I ran into the same issue, now I am in the process of doing a clean install of 8.04  Good Luck.

---

### Post by sc_dan2002 on 2009-01-25
Ha!

This is great... spent a week trying to get wireless working on 8.04... almost a week trying to get graphics to work on 8.10.

So I'm left with the choice: 
8.04 and no internet
8.10 and no gui (so no internet)

Oh what fun...

---

### Post by LardElbow on 2009-01-26
Not sure if this will help but I had the same problem with a hybrid card setup (nvidia 9600M GT and a bog standard intel graphics chipset). To get around it I had to deactivate the intel chipset via the bios. Once this was done I could start the desktop. I notice in your setup you have two nvidia cards, maybe disable/remove one and see how it goes.

---

