---
title: "Stuck at BusyBox after a kernel reconfigure and migration to EXT4...?"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by shgadwa on 2009-03-21
Let me explain:

I installed Ubuntu 8.10 on this here Toshiba Satellite PRO L300 Laptop, 1.86Ghz dual core CPU, 1 GB RAM... lots of hard drive space.

It all worked fine until I decided to reconfigure my Linux Kernel (and upgrade to the latest 2.6.28 kernel instead of the .27 one.) I also migrated to EXT4 using a very simple guide and that worked fine.

I think somehow, I messed something up though. I think it might have something to do with their being so many different kernel sources in the /usr/src and /usr/src/linux folders from various attempts at configuring the kernel so that it is 'just right.'

Normally, I have never had any problems configuring the kernel, but this is different. I used this thread [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

And it did bring up a couple errors after I did cd .. && dpkg -i linux*2.6.28*.deb, but I do not remember what it said.

Anyhow, when I try to load the latest kernel I have, it goes to BusyBox and says

Loading, please wait...
Gave up waiting for root device. Common problems:
  - Boot Args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/5ba5e6e9-b227-4a41-be06-e0ea9e550531 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu...... blah blah blah.


Any help would be appreciated.

---

### Post by shgadwa on 2009-03-22
I should note that my other Ubuntu Kernels do not work on here either... probably because they do not have EXT4 support.

EDIT: I can CHROOT into the system using a LiveCD...

---

### Post by dandnsmith on 2009-03-22
> **shgadwa said:**
> 
It all worked fine until I decided to reconfigure my Linux Kernel (and upgrade to the latest 2.6.28 kernel instead of the .27 one.) I also migrated to EXT4 using a very simple guide and that worked fine.
...

Anyhow, when I try to load the latest kernel I have, it goes to BusyBox and says

Loading, please wait...
Gave up waiting for root device. Common problems:
  - Boot Args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/5ba5e6e9-b227-4a41-be06-e0ea9e550531 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu...... blah blah blah.

Whatever about the other problems, I wonder if you've changed the UUID of a vital partition with the conversion.

I'd try using the install/liveCD  as a live system and look at the grub config file, the UUIDs of partitions (ls -l /dev/disk/by-UUID) and other info to see if you can verify it.

If you find it, I'd edit the (installed) /etc/fstab entries to get them correct, and then try the boot again.

---

