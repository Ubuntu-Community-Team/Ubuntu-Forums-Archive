---
title: "Does Wubi do anything unusual with disk mounting?"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2009-07-31
Hi All,
I have been struggling to fix an issue whereby one of my NTFS drives does not appear as a location that can be mounted.

After a lot of great help from nikhilk, we worked out that the drive in question has been mounted twice somehow.

I was going to try disconnecting, but it occured to me that this might be something that was done by Wubi, to do it's clever stuff. (It's a Wubi install, I get very nervous about disk partitioning, and I am a big fan of the Wubi approach).

So the obvious question is, could this be something that Wubi needs?

Information:

Output of cat, (with sdb1 lines in bold):

nick@ubuntu:~$ sudo cat /proc/mounts
[sudo] password for nick: 
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=755 0 0
**/dev/sdb1 /host fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,b lksize=4096 0 0**
/dev/loop0 / ext3 rw,errors=remount-ro,data=ordered 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
varrun /var/run tmpfs rw,nosuid,mode=755 0 0
varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.28-14-generic/volatile tmpfs rw,mode=755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
**/dev/sdb1 /boot fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,b lksize=4096 0 0**
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,b lksize=4096 0 0
/dev/sdc1 /media/sdc1 fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,b lksize=4096 0 0
/dev/sda1 /media/sda1 fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,b lksize=4096 0 0
/dev/sda2 /media/sda2 fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,b lksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
gvfs-fuse-daemon /home/nick/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user_id=1000,group_id=1000 0 0
nick@ubuntu:~$ 

And the thread this came up in is here:
[http://ubuntuforums.org/showthread.php?t=1224213&page=2](http://ubuntuforums.org/showthread.php?t=1224213&page=2)

All clues very gratefull receieved!
Thanks, Nick

---

