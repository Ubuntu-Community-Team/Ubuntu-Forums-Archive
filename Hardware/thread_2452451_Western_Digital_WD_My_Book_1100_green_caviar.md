---
title: "Western Digital WD My Book 1100 green caviar"
date: 2020-10-22
forum: Hardware
---

### Post by christon74 on 2020-10-22
Good afternoon fellow Ubunters):P I'm trying to resuscitate a WD My book and I have launched "scrub" in a terminal window (nnsa option). The problem is that I cannot see the progress. Is there a way to actually see the progress in a second terminal window. With dd, the syntax is                         dd if=/dev/urandom | pv | dd of=/dev/null
Oh! I have tried this 
                        sudo scrub if=/dev/urandom | pv | scrub of=/dev/null
 and the terminal shows that there is absolutely nothing going on.  I have to try something else. 
Have a nice Thursday, all of you.;)

Uh? I launched ddrescue nearly 4 hours ago. This WD hard disk is 750 Gb big, but dd still goes on and now shows 870 Gb!! How can that be?

---

### Post by TheFu on 2020-10-22
Did you want to wrte to the hdd?  none of those commands do that. They write to a pseudo-device /dev/null.  /dev/null just eats anything sent to it. It doesn't save anything. It doesn't hit any storage or RAM.

I don't know scrub.

So, first thing is to determine the device name ***now**.  Then plug the partition device, probably something like /dev/sdj1, into the dd command.  sdj1 most like is NOT to correct device.


The example command would be 
```
sudo dd if=/dev/urandom of=/dev/sdj1 bs=4m
```

To determine the partition(s), there are multiple ways.  lsblk, fsdisk, parted, gparted, or watching the dmesg output as the USB is connected. Devices change, so don't assume the answer yesterday is still correct. Rebooting or disconnecting/reconnecting often change the device name.

---

### Post by TheFu on 2020-10-22
BTW, if you pick the wrong device, it will be very bad.  Total data loss. This is serious.  Be very careful.

---

