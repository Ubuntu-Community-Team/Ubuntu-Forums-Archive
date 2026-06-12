---
title: "PS/2 devices occasionally not detected at boot"
date: 2009-10-26
forum: Hardware
---

### Post by mvanbem on 2009-10-26
I have an MSI GT735 laptop which works reasonably well with Ubuntu 9.04, but has a few weird issues. Sometimes I boot the machine and find that the keyboard and touchpad aren't responding when GDM comes up. I did some googling and saw that it could be related to the PS/2 controller. After a fail-reboot cycle, I saw that /var/log/syslog contained lines with 'i8042', but /var/log/syslog.0 didn't. Assuming there was something going on with the i8042 driver, I tried booting with the 'i8042.debug' flag, but after several reboots I have been unable to reproduce the issue.

Keeping the debug flag on appears to suppress the problem, but I would like to find out what is actually going on. What should I do next?

I'm also having two other maybe-driver-related issues. Should I open separate threads for them?

---

### Post by em3raldxiii on 2009-11-13
Hi mvanbem,

I too have the MSI GT735.  I had troubles with audio not working correctly, but nothing precisely like you are having, which I think is kinda strange.  However, I did want to recommend that you try upgrading to the newest 9.10 Karmic Koala.  I found that once I upgraded, nearly all of my problems (most of them minor anyway) completely vanished.  To me, this latest upgrade has been a truly fantastic experience with this laptop.

I hope that helps a little!

---

