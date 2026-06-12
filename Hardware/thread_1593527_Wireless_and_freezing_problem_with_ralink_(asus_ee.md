---
title: "Wireless and freezing problem with ralink (asus eeepc) and maverick meerkat"
date: 2010-10-11
forum: Hardware
---

### Post by enigmatichus on 2010-10-11
Hello, I'm dealing with a pretty good problem. I've installed a few minutes ago maverick meerkat (32 bit) on my Asus eeepc 1001HA (I previously used lucid lynx without any issue, despite of the need for a manual driver installation for the internal wireless card) and everything went well with the installation. Even wireless, which in the previous release had to be manually installed, works now, but I've a big problem: I actually cannot turn off the computer, nor reboot it or put it in standby. I cannot do anything concerning the shutdown and I was not able to turn it off neither using console commands (shutdown, halt, reboot) and trying to launch halt command from another virtual console (ALT+F1), just before the system completely freezes out I get this error: "phy0 -> rt2800_wait_wpdma_ready: error - wpdma tx/rx busy, aborting"
Even trying to disable the wireless from the network applet causes the system failure. Please help me, I even tried to reinstall again ubuntu and I simply have the same problem. I don't know how to do.
Thank you anyway!

---

### Post by db260179 on 2010-10-12
Just upgraded from 10.04, had same problem as yourself.

Reported bug of this problem - conflicting drivers. Do as follows

open up terminal

type

sudo nano /etc/modprobe.d/blacklist.conf

add the following at the bottom

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

save file ctrl+o then ctrl+x, reboot (hold power button to force shutdown)

boot back up should be ok.

Hope this helps?

---

### Post by enigmatichus on 2010-10-12
> **db260179 said:**
> Just upgraded from 10.04, had same problem as yourself.

Reported bug of this problem - conflicting drivers. Do as follows

open up terminal

type

sudo nano /etc/modprobe.d/blacklist.conf

add the following at the bottom

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

save file ctrl+o then ctrl+x, reboot (hold power button to force shutdown)

boot back up should be ok.

Hope this helps?

Thank you very very much, man!! It worked absolutely flawlessy!! :)
Thank you for the fast solution you gave to me!

---

### Post by gargok on 2010-10-14
Thank you, [db260179]("http://ubuntuforums.org/member.php?u=265561")!!
It worked :guitar: Great and fast response!

---

### Post by db260179 on 2010-10-15
thanks guys!

Hope it helps alot?

---

### Post by enigmatichus on 2010-10-15
It definetely helped a lot! 
Thank you again! :)

---

### Post by iancs2009 on 2010-10-22
:guitar:

Oh yes, you rock so hard it must hurt! - 
I was having the same trouble with a Compaq CQ10-400.

Worked here too, many thanks!

Ian

---

### Post by ntanitime on 2011-05-29
thanks to you too from italy!!!:guitar::guitar:
I had the same problem !!

---

