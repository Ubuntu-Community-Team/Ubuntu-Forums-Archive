---
title: "some freezing during boot up"
date: 2010-02-08
forum: Hardware
---

### Post by Hansmc on 2010-02-08
I ask this earlier under dell form and got no reply, so I will try here. It is on a dell Inspiron 13. Worked fine on last Ubuntu, but ever since did a clean install a few months ago, it will freeze during the boot, after the screen where you can select the different operating systems. Then we have to do a hard reset. Some times it will go half a dozen times with out any problem. At other times we will have to try half a dozen time to get it to complete a boot.

One time it did not boot the OS at all and we got this:


> Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdlines)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/d81f415e-2588-4a88-9953-e23894324489 does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Any help? Thanks

---

### Post by pi/roman on 2010-02-08
It almost seems to random for a software problem.  Maybe it is a loose hard drive cable.  I wonder if the older version would still work, maybe you could test it in live cd mode.

---

### Post by adam814 on 2010-02-08
+1

That's most likely hardware flakiness (or cable).  It could have to do with any BIOS settings related to your HD controller as well I suppose, but that wouldn't change randomly (at least I hope not).

The only other possibility I'm seeing here is an initrd missing your controller drivers.  You could rebuild it just to be safe:
```
sudo update-initramfs -u -k `uname -r`
```
Obviously that requires your system to boot first though.

---

