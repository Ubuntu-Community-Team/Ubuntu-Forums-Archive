---
title: "Can't boot after 9.04 upgrade"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by meinzy on 2009-04-30
Can't get anywhere after using Update Manager to upgrade from 8 to 9.  I get the following screen after ~ 20 seconds of it appearing to be booting:

[COLOR="Red"]Boot from (hd0,0) ext3   50536b4e-6bed-4e53-879c-54e7cdf2dd6e
Starting up …
Gave up waiting for root device.   Common problems: 
  -Boot args (cat /proc/cmdline)
     - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for the right device?)
   - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/50536b4e-6bed-4e53-879c-54e7cdf2dd6e does not exi
opping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-on commands.

(initramfs)[/COLOR]


My keyboard won't work, so can't do anything.  I'm a noob and don't understand the command line information above.

---

### Post by reja on 2009-05-01
Same exact problem here. 8.10 was running fine, but after the upgrade to 9.04, I got the same error as above. To try and fix, I booted from a live CD, but it no longer sees my hard drive at all. (It has no problem reading my external hard drive, which is USB.) From the live cd, hoping to get it to read the hard drive, I installed/ reinstalled samba and did a dist-upgrade. No success. It almost seems like once 9.04 gets past the boot script, it doesn't see or can't access the hard drive.

Of possible importance: my hard drive was partitioned into three partitions. The first partition had the current operating system, and the second partition had an older copy of Ubuntu (8.04, I think). The grub menu lists the OS from both partitions, but none will boot now.

Thanks for any help.

---

