---
title: "upgrade from 9.04 to 9.10 boot only to terminal"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by ioasw on 2009-10-31
I had 9.04 installed on an HP tx2510us with ATI zorg graphics installed.  I did an internet upgrade to 9.10, and the screen turned on and off after reboot.  I rebooted into recovery mode and removed and reconfigured the xorg ATI driver, and now I only get a boot into terminal.  Can anyone help with this?  Are there commands I need to give in terminal start up into 9.10?

---

### Post by ioasw on 2009-11-01
bump

---

### Post by bbiggers on 2009-11-01
Looks somewhat similar to my situation (still awaiting solution):

[http://ubuntuforums.org/showthread.php?t=1308936](http://ubuntuforums.org/showthread.php?t=1308936)

Do you get prompted for your username and password before going to terminal?

---

### Post by Sunflower1970 on 2009-11-01
I just left a message over there since I was having a similar problem. Only difference is I had an nvidia card.

---

### Post by jwang on 2009-11-01
You should find some useful information in /var/log/Xorg.0.log.
If you're lucky, maybe this is just due to incorrect statement syntax in /etc/X11/xorg.conf(you should be able to know in Xorg.0.log); If you're unlucky, maybe this is the driver's problem and probably will not get a prompt fix.

---

### Post by ioasw on 2009-11-01
Thanks for all the input, and yes I do get prompted.  I have had trouble with the xorg.conf file in the past so maybe that is the problem for right now I'm going to boot up into terminal and reinstall the xorg driver.  Let me know about any updates.

---

### Post by ioasw on 2009-11-01
so I reinstalled the xorg driver and now I get my screen turning on and off again (that is what I had before I uninstalled it) so it is the video driver, so I guess that's better than a bad install, but then again we could be waiting for a new driver to be written.  I'll keep you posted on any updates I get.
 
For my next act I wil run the ubuntu 9.10 cd and see if I can install a different driver that way.

---

