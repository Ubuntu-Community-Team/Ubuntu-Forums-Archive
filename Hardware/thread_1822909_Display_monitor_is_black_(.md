---
title: "Display monitor is black :("
date: 2011-08-11
forum: Hardware
---

### Post by the_jav on 2011-08-11
Hello everyone,

I need to find where the display screen configuration file is stored in the Xubuntu preferences in order to delete this file because I did a mistake : I unchecked "use this monitor" in a setting panel and from that moment, my screen is always black (even after a reboot).

I am on a MacbookPro and I have a dual-boot on MacOSX and Xubuntu 11.04 but I'm not sure it changes something...

Thanks in advance for your help :-)

7av

---

### Post by Toz on 2011-08-11
Possibly **~/.config/xfce4/xfconf/xfce-prechannel-xml/displays.xml**?

---

### Post by the_jav on 2011-08-11
Thank you very much !!

That was exactly this file. I deleted it (with a live CD) and after the reboot, the display was working again !

Again, thank you :-)

---

