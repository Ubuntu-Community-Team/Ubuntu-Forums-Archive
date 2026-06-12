---
title: "Grub can't find mdadm raid md1 after making md2 with webmin"
date: 2014-01-23
forum: Hardware
---

### Post by jerryriggin on 2014-01-23
I installed 12.04 server with raid 1 on installation, creating MD1.  Got 2 new drives and made them raid1 with Webmin.  Everything was fine -- I could use both array's until I rebooted the box.

Now, on boot, grub can't find /dev/disk/by-uuid/c232c69-7edf--4795-b600-72c6686- 8692ee2... dropping to shell!  
I tried live Boot Repair -- it did nothing but post [http://paste.ubuntu.com/6805352](http://paste.ubuntu.com/6805352) and say "No change has been made to your computer."  

Boot Repair CD GParted says sda2 and sdb2 are both boot, raid but can't identify file system (it is ext4).  (dev sda1 and sdb1 are a raid 1 swap, which may not have been a good idea?)

I boot from the live CD, but "System Rescue" won't mount anything as root fs.  When I drop to a shell and try to mount anything, it is "busy".  When normal boot drops me to busybox, I can't find a way to edit grub or run grub-update, or run fsck.

Update:  I pulled one of the raid drives in md1 and put it in a 12.04.1 kubuntu workstation.  KDE Partition Manager 1.03 shows the drive partition sda1 as 29.8 GiB  linuxswap with flag "raid", but it sees sda2 as 1.79TiB with "unknown" file system type and flags "boot, raid"

---

