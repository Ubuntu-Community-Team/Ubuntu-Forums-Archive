---
title: "Wierd message 9.10 wireless setup"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Z06Gal on 2009-10-22
I can't seem to get my wireless going with 9.10 and when I try to put the info in manually, I get this message:

Error editing connection: property '%s' / '%s' invalid: %d
NMsettingWireless

Anyone have a clue?  I have commented out the bcm43xx line from this command  gksudo gedit /etc/modprobe.d/blacklist.conf but still nothing.  This is so frustrating.  

Robin

---

### Post by itsjareds on 2009-10-22
Which wireless card do you have, and which module does it use? If you have not restarted your computer after commenting that line from blacklist.conf, you still need to disable that module for your current boot session:
```
sudo rmmod bcm43xx
```

If you need to enable your wireless card's module, do this by entering:
```
sudo modprobe MODULE
```

Where MODULE is your module's name.

---

### Post by Z06Gal on 2009-10-22
I got it going finally.  Updating and rebooting seemed to do the trick.  Thanks. 


Robin

---

