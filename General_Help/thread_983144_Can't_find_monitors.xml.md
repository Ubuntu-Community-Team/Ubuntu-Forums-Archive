---
title: "Can't find monitors.xml"
date: 2008-11-15
forum: General Help
---

### Post by Daldana on 2008-11-15
Hi all, I'm using Intrepid and messed myself up. I hooked up a Vizio 42" TV to the box and it worked great but needed to have the resolution changed. Unfortunately, I changed it too high and can't see the screen long enough to make the change back; the desktop flashes for a second or two then goes away. I can use a regular monitor without a problem, if I use ctrl+alt+F3 with the Vizio hooked up, I can see the screen just fine.

I've used the dpkg-reconfigure -phigh xserver-xorg, tried to copy the xorg.conf.failsafe file, and tried to boot with the CD, all to no avail. It seems that the system tries to detect the monitor and set it to its last settings (which are wrong).

I saw somewhere that there is a monitors.xml file that contains the settings for each monitor, but I can't find it anywhere.  Any ideas?  Thanks.

Dave

---

### Post by parr on 2011-11-03
Is anyone finds this...
The monitors.xml file is located at //home/[home account]/.config/monitors.xml.

---

### Post by oldos2er on 2011-11-03
Closed, please don't bump old threads.

---

