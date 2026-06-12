---
title: "HP Proliant 380 G6 reboots almost daily"
date: 2014-03-24
forum: Hardware
---

### Post by 7sbaV8Kt5PTh on 2014-03-24
We're running Solr on Ubuntu on DL380 G6 with 72 Gigs of Ram and 16 cores.  For some reason, just about every day, it spontaneously reboots.  When it reboots, is is so quick that it doesn't write to the logs.  I've read quite a few articles about this and it seems to be pretty common.  I've added two lines to the bootloader GRUB:

acpi=off
intremap=off

However, this doesn't seem to help.  Have any of you seen this?  Any suggestion would be helpful, even advice on how to figure out what it really is...

---

### Post by gifford on 2014-03-24
Has the firmware been updated? Here is a link that might help:[http://serverfault.com/questions/235732/2008-sever-randomly-reboots](http://serverfault.com/questions/235732/2008-sever-randomly-reboots)
Also, has Ubuntu been updated as well? I am using an HP xw8600 and had the problem initially using 12.04. It was a bug that was taken care of with the updates of 12.04.

---

### Post by 7sbaV8Kt5PTh on 2014-03-24
Hi, Gifford, I should have mentioned that.  The firmware is up to the latest, as is the OS, at 12.04.4 LTS.  I'll have the hardware guy check the serial, but I'm almost positive, it was built mid-2010.  But, since I'm old, I'll "trust but verify".  Thanks!

---

### Post by gifford on 2014-03-25
Not sure what the problem is. How is the power unit? In some of the google reading it mentioned defective power units.

---

### Post by 7sbaV8Kt5PTh on 2014-03-25
I think some have mentioned the power management in the BIOS.  I'm having the hardware guy check that out (it's in a DC, several hundred miles away).  We made it a whole day without it rebooting yesterday.  :D

---

