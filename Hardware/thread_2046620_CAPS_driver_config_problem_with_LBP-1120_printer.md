---
title: "CAPS driver config problem with LBP-1120 printer"
date: 2012-08-23
forum: Hardware
---

### Post by Diskdoc on 2012-08-23
I followed the guide here: [https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install]("https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install")

But my problem is this: I can only get printing to work if I do "sudo service ccpd start" after I boot the computer. Trying to get ccpd running automatically from /etc/rc.local (as stated in the CAPS driver readme) or trough update-rc.d gives me only one malfunctioning ccpd process.

Suggestions?

I added "lpusb" to /etc/modules and kept "/etc/init.d/ccpd start" in /etc/rc.local. Finally..! It does seem to work like a printer should now.

(edit)

..once, at least. Usually I ended up with only one ccpd process anyway! I added "sleep 5" to my rc.local before ccpd starts. Not a nice solution but it seems to work so far..

---

