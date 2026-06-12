---
title: "MAKEDEV won't create md devices"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by daehenoc on 2009-06-28
Hi all,

I'm trying to install Mythbuntu 9.04 to a pair of 750Gb HDDs in RAID1 (/dev/md1 is /boot, /dev/md2 is /).  During the install process, I have to install mdadm to get the raid devices going, and all appears well.  However, when I chroot to the target system and install mdadm there, I get a message that MAKEDEV doesn't exist.  (The devices exist during the install process, inherited from the installer environment.)

On boot, I get the following:
```
Gave up waiting for the root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/md2 does not exist. Dropping to a shell!
```
Examination reveals that the raid1 module is loaded, but /dev/md1 and /dev/md2 really don't exist.

Doing the same installation off the Ubuntu 9.04 amd64 alternate CD results in a working system!  How do I create the /dev/md1 and /dev/md2 devices on the HDDs?

Thanks,
Greg

---

### Post by daehenoc on 2009-06-28
Fixed!

For some reason, the Mythbuntu CD doesn't update /etc/mdadm/mdadm.conf 
with the definition of the arrays for /dev/md1 and md2.  ("ARRAY 
/dev/md1 level=raid1 num-devices=2 UUID=04xx..")

What I did was install Ubuntu on /dev/md[56] (made up of 
/dev/sd[ab][56]) and have a look at what was in /dev/mdadm/mdadm.conf. 
Once I saw what was missing from mdadm.conf on /dev/md2, I copied the 
ARRAY line from mdadm.conf on /dev/md6 to /dev/md2 and 'dpkg-reconfigure 
mdadm' from the chroot.

Now MythTV is booting just fine and dandy off the correct md :)

---

