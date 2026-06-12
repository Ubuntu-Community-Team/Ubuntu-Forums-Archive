---
title: "upgrading my video card"
date: 2008-07-22
forum: Hardware
---

### Post by Mr Pockets151 on 2008-07-22
Right now I have an ATI x1550 chipset video card.  I want to upgrade to the  GeForce 8600 GT 256 MB card (XFX card).  Will this be a problem that anyone knows about.  I checked the Hardware Support WIKI and it states that the GeForce 8600 GT 512 is compatible with Gutsy so I assume that the card I want should be okay.

Is it going to be a problem to upgrade on a dual boot system?

What about GeForce 8500

---

### Post by Rocket2DMn on 2008-07-23
AFAIK, I have heard that it is NOT supported in Feisty, but if you say it's good in Gutsy, then go for it.  I know it works in Hardy because I have that card on a Hardy install.
Before you make the switch, you should uninstall the restricted fglrx drivers, then reconfigure X with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
At this point, shut the computer down and make the card switch, then boot back up.  You should now be able to login and install the restricted Nvidia drivers.

---

