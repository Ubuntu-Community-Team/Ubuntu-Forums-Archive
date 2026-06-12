---
title: "HELP:  How to rebuild degraded RAID array?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by theosib on 2009-04-18
I've been tearing my hair out trying to figure out how to rebuild a degraded RAID1 array.  Every how-to I find seems to make assumptions about mdadm that are different from how Ubuntu configures it.  For instance, /etc/mdadm/mdadm.conf usually lists the devices that are in the array.  Instead, this one just says "DEVICE partitions".  When I "cat /proc/mdstat", I expect to see the names of devices like /dev/sda2 and such listed, but instead, I see "dm-1".  Plus, while there's a /dev/sda, there is no /dev/sda2.  I can't seem to get mdadm to tell me what are the names of the devices that SHOULD be in the array.  Just that it's degraded.  So I can't figure out what command I should type to add back the missing device to the array, because there just don't seem to be any device names.

Can anyone help me out here?  This is all very confusing.

Also, isn't there some automatic or GUI-based way to manage this?

---

### Post by ronparent on 2009-04-22
Try [http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)

Incidently, dm-1 is a sybolic link which is your raid array. The actual partitions are contained within that array.

---

