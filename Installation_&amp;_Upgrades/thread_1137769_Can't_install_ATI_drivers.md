---
title: "Can't install ATI drivers"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Moohasha on 2009-04-25
I just installed Ubuntu 9.04 on my OLD Dell Inspiron 9300.  I'm trying to install the drivers for my video card now.  I tried System->Administration->Hardware Drivers, but nothing is listed there.  So I downloaded the drivers myself from ATI's website and tried to install them, but I get this error message:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

I found this thread with the same issue:  [http://ubuntuforums.org/showthread.php?t=970059](http://ubuntuforums.org/showthread.php?t=970059)

Judging by that thread, does that mean that I just can't install the ATI drivers right now??  I'm a complete n00b to Linux, so I don't understand anything that's going on.  Any help would be appreciated.

---

### Post by Mark Phelps on 2009-04-27
Don't know what video chip your Dell uses, but the most current ATI drivers (Catalyst 9.4) have dropped support entirely for "older" chipsets. I have a 2 year old card and even it is not supported anymore.  

You're probably going to be stuck using open source drivers.

---

### Post by Dearhell on 2009-04-27
I have also a Dell 9300 Inspiron with an ATI x300 and I have the [same problem](http://ubuntuforums.org/showthread.php?t=1138302).

---

### Post by apparle on 2009-04-27
Ubuntu 9.04 has upgraded X.org .
The new version of X.org is supported only by 9.4 version of ATi drivers and not by 9.3 or previous
But Ati has put many cards into legacy(unsupported and non-updated) and hence 9.4 version only supports the latest cards.
So whoever has a card which is the not supported by 9.4 cannot install fglrx drivers.. :(

Try Open Source Drivers................:)

---

### Post by Moohasha on 2009-04-29
I rolled back to 8.04 and was able to install the drivers.  Unfortunately, that didn't resolve the ulimate problem I was having with graphics in a game running with Wine, but that's a different issue. :(

---

### Post by oldrocker99 on 2009-04-29
I rolled back to 8.10 and it looks like I'm going to stay there (using ATI drivers v9.01, which still support my laptop's X1200 card (and the new ones DON'T:confused::confused::confused:)), so I have OpenGL working and can enjoy compiz, etc.

I like a few of the features of 9.04, but it certainly wasn't enough of a major upgrade for me to put up with its nonsupport of ATI's fglrx drivers.

:guitar:

---

### Post by emarkay on 2009-04-29
This thread is the focus on th ATI/AMD issues:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

