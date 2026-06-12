---
title: "ati drivers for radeon x1200"
date: 2009-06-16
forum: Hardware
---

### Post by linux_08 on 2009-06-16
hello all...

im tryng to install the ati drivers for linux its version 9.3...i have ubuntu 9.04 and when i log in as root and run the command this is what i get....and ideas wat im doing wrong? I'm using this driver 

ati-driver-installer-9-3-x86.x86_64.run


Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being correctly set by --iscurrentdistro

thanks

---

### Post by rizman on 2009-06-16
The catalyst 9.3 drivers will not work with Ubuntu 9.04 because Jaunty uses version 1.6 of X Server. Unfortunately, the 9.3 drivers are not compatible with XServer 1.6 (for a reason I don't know and I probably will not understand :-) ) XServer 1.6 will only work with version 9.4 and higher of the catalyst drivers. However, you card (the X1200) has been put on legacy support by AMD/ATI as of catalyst 9.4.

Thus, you are left with 2 options:
1) Install Ubuntu 8.04/8.10 with catalyst 9.3 (that's what I did in the end)
2) Use the open-source ati drivers. Those work very good with 2D and some basic 3D is implemented. However, if you need advanced 3D effects (cf. Shaders etc...) those might not work very good. At least on my Mobility X700, 3D performance was very poor with the open-source drivers, hence my move back to Hardy Heron.

---

### Post by masux594 on 2009-06-16
Try to install the RadeonHd drivers.. I've x1950 and ati drivers don'r run correctly on my jaunty x64.. Installing [RadeoHD]("https://help.ubuntu.com/community/RadeonHD") drivers with this guide, i've no problem.. maybe little less performance, but, i use pc mainly for working.. Obvious that I've installed compiz with many effects and all work pefectly! Your x1200 [not "mobility"] isn't in the supported hardware but, just try.. 

A

---

### Post by linux_08 on 2009-06-16
thanks to both of u guys

@masux594

thats too complicated..but thanks for the help...i have a toshiba laptop p205d 7454 and the old version of ubuntu worked fine....this new version is as slow as the other one but video drivers are killing me.... :-(

---

### Post by masux594 on 2009-06-17
Nothin' is too difficult! remember "Impossible is nothing!".. Yes, IMHO drivers are the more difficult things in ubuntu.. But from the previous release they have been made great steps!! 

If u have this laptop, it means that u heve the **MOBILITY** ati radeon x1200.. The RadeonHD support your hardware configuration, if u want, you can resolve the problem following step by step [the guide]("https://help.ubuntu.com/community/RadeonHD") [it **looks** hard], or grope in the dark without success..

Your choose: 
> *You take the blue pill, the story ends, you wake up in your bed and believe whatever you want to believe. You take the red pill, you stay in Wonderland, and I show you how deep the rabbit hole goes*
[matrix rule 8)]

Sysc, A

---

### Post by Yellow Pasque on 2009-06-17
The radeonhd driver is worth a try if you value stability, Jaunty compatibility, and/or 2D acceleration over 3D acceleration.

I started the RadeonHD guide (and got some nice suggestions from the gurus), so if you have suggestions for making it more n00b-friendly, I'm open to them. Perhaps I should put the pre-built .deb section first?

---

