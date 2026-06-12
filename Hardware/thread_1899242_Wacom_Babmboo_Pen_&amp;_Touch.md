---
title: "Wacom Babmboo Pen &amp; Touch"
date: 2011-12-23
forum: Hardware
---

### Post by gabrielshier on 2011-12-23
Hey, 

Just got a brand new Wacom Bamboo and Ubuntu kinda got me down. As always we have the incredible argument that linux is simply better than Windows. The intallation of the Bamboo should have been simple. 
Can't seem to get it working thought.
So; kernel: ```
2.6.32-37-generic-pae
```
Ubuntu 10.04.3 LTS.

Added the repository and installed what was asked:
```
sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install wacom-dkms
```

Still not working. Tried a few other tutorials, all the same. 
```
xsetwacom list devices
``` - gives nothing back.
Listing USB devices gives:
```
root@XXXXXX:/home# lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 056a:00de Wacom Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Can anyone please tell me what am i doing wrong?
Nothing seems to work.

---

### Post by Favux on 2011-12-23
Hi gabrielshier,

Your model is new as of October this year.  So it is not even in Oneiric's kernel driver/module wacom.ko.  And DoctorMO's PPA is much too old to have a model that new in it.

Support for the DE was added in input-wacom-0.12.0, currently at 0.12.1.  So you would need to compile that, see the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

However Lucid with the 2.6.32 kernel is not supported for the second generation BambooPT's touch or your third generation BambooPT because it lacks the mt.h.  The multi-touch header first becomes available with the 2.6.38 kernel i.e. Natty.  Which means your model tablet is not supported in Lucid or Maverick and there is no plan to do so that I know about.

---

### Post by gabrielshier on 2011-12-23
Hi Favux,

Sorry for my ignorance, but what does that mean?
That i need to update kernel? Upgrade to 11.10? Nothing i can do since that are no drivers yet?
What would you recommend?
And thanks a lot for the expert response :)

---

### Post by Favux on 2011-12-23
It means to get your tablet working you need to upgrade to at least Natty.  Might as well make that Oneiric since it is so much better than Natty.  Then follow part I. and part II. (actually cloning xf86-input-wacom which is appendix 1 would be better) in the BambooPT HOW TO.

---

