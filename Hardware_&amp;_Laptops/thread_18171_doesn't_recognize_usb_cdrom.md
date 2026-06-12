---
title: "doesn't recognize usb cdrom"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by lorap on 2005-03-05
maybe somebody knows the way to solve my only problem.
thanks
pavel

---

### Post by alastair on 2005-03-05
Logs ....

Have a shell open - "tail" your syslog fiel so you can see messages from the kernel as they happen i.e.

sudo tail -f /var/log/syslog

Plug in the CDROM and look for messages. Anything?

---

### Post by lorap on 2005-03-05
this's the message i receive when trying open CD2 (ubuntu did recognize i do have 2 cdroms):
mount: special device /dev/scd0 does not exist
pavel

---

### Post by alastair on 2005-03-05
Before creating any special devices, have a look at the BOOT messages - either via :

dmesg

or

<edit> /var/log/syslog

Look for the IDE discovery - and see what devices it thinks you have (CDROM, disks etc.) i.e. "Probing IDE interface" etc.

Also, if you plug/unplug your USB CDROM - see what messages are written to the log when you plug it in (as per my message above).

Also, what version of Ubuntu.

---

### Post by alastair on 2005-03-05
Sorry - if it is USB - forget the "IDE discovery" bit.

But - with the CDROM not plugged in - look at the messages printed in /var/log/system WHEN you plug it in.

---

### Post by lorap on 2005-03-05
thanks friend i'll do it.
don't really know what's wrong with it.
usb cd isn't something rare.
thanks again.
pavel

---

