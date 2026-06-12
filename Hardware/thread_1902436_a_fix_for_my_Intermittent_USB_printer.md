---
title: "a fix for my Intermittent USB printer"
date: 2011-12-30
forum: Hardware
---

### Post by sprog on 2011-12-30
After upgrading to 10.04 (maybe 10.10) printing to my HP Laserjet 6L became intermittent.  On very rare occations it worked.   It is connected via a Belkin USB to parallel lead.  The computer is currently running 11.10.

After 18 months of trying this and that, the following fixed it for me: 
lsusb
displays: Bus 002 Device 004: ID 050d:0002 Belkin Components 
sudo chmod a+w /dev/bus/usb/002/004
and it is fixed!  at least right now it is.

Apparently if I make "lp" the group, and add write access to the group:
there is no need to chmod again.

...someone elses example:
~$ ls -l /dev/bus/usb/004
total 0
crw-rw-r--  1 root root 189, 640 2010-10-11 23:09 001
crw-rw-r--  1 root root 189, 641 2010-10-11 23:09 002
crw-rw-r--+ 1 root lp   189, 642 2010-10-12 00:14 003

---

### Post by zcacogp on 2013-02-12
Sprog, 

Many thanks for this - it has helped me enormously. I think it is the solution to an intermittant printing problem I have in 12.10. 

However, the magic only lasts until the next reboot. After it has rebooted the intermittant problem returns. 

I can see a list of items on the USB hub, similar to those listed in your last post, like this: 

```

ogp@desktop:/dev/bus/usb/004$ ls -l
total 0
crw-rw-r--  1 root root 189, 384 Feb 12 14:29 001
crw-rw-r--+ 1 root root 189, 385 Feb 12 14:29 002
crw-rw-rw-  1 root lp   189, 386 Feb 12 18:54 003

```

What do you mean by "Apparently if I make "lp" the group, and add write access to the group:
there is no need to chmod again." Is this the permanent solution to the problem? 

Thanks again. 


Oli.

---

