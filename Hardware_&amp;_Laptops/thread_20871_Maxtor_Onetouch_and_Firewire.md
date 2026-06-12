---
title: "Maxtor Onetouch and Firewire"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by jasplund on 2005-03-19
I have a Maxtor Onetouch external drive which I can't get to work with firewire. It works with USB though. But since I only have USB 1.1 it's very slow. Ubuntu detects it as Onetouch (see screenshot) but i doesn't mount it. It works with firewire in SuSE on the same computer

---

### Post by alastair on 2005-03-19
Which version of Ubuntu? The next/new version (5) might be better - but Linux and firewire is still a bit fragile unfortunately.

Boot with it plugged in and checkl the system logs :

/var/log/syslog

See if any reports from firewire or SCSI subsystem.

Perhaps also boot without it, then login and open  a shell - then :

sudo tail -f /var/log/syslog

Plug it in - and see if any messages are printed in the syslog.

---

