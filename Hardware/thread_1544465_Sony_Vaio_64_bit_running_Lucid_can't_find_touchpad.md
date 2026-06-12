---
title: "Sony Vaio 64 bit running Lucid can't find touchpad"
date: 2010-08-02
forum: Hardware
---

### Post by tankjl on 2010-08-02
I know the touchpad works because it is fine in Windows but in both the 32 bit and 64 bit installs I tried it did not find the touchpad. The GUI in Gnome does not show the touchpad and an xinput --list does not show a touchpad or mouse other than the usb mouse attached. 
dmesg | grep -i touchpad shows nothing either. This is a brand new laptop i7 quad core. there are the following files in the /usr/lib/X11/xorg.conf.d dir
 
10-wacom.conf, 10-synaptics.conf 10-vmmouse.conf 05-evdev.conf
 
I tried loading the various touchpad related modules from the package manager to no avail.
 
Thanks
 
Jeff

---

### Post by MasterGamerJK on 2010-08-02
try 32-bit???   maby a live cd (cant hurt to try)

---

### Post by corrytonapple on 2010-08-02
Have you installed drivers? 
> **MasterGamerJK said:**
> try 32-bit???   maby a live cd (cant hurt to try)
It was noted that 32-bit was tried.

---

### Post by tankjl on 2010-08-02
found the work-a-round here..[http://ohioloco.ubuntuforums.org/showthread.php?p=9670099#post9670099](http://ohioloco.ubuntuforums.org/showthread.php?p=9670099#post9670099)
 
gives limited support. the entry in the Xorg.0.log shows a "jogdial" which is the touchpad on the Vaio F series. No scrolling and such but at least it works for basic functions.
 
Thanks
 
Jeff

---

### Post by corrytonapple on 2010-08-02
Be sure to mark it as solved. Thread Tools at top of page, then mark as solved.

---

