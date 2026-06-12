---
title: "Startup error, dropping to a shell!"
date: 2008-10-31
forum: General Help
---

### Post by Galzo on 2008-10-31
Hi everyone, 

First, I must said I'm newbie to Ubuntu, just use it for a few days. And I don't know what exactly cause the problem I will describe below. Hope you can help, thanks in advance :).
My system:
Installed Vista at drive C:, wubi install at drive F:\ubuntu
Using chip AMDX2, main ASUS M2N-E

I installed Wubi 8.04 before and have no problem. When Wubi 8.10 available, I uninstall 8.04, delete backup folder and install new wubi 8.10 with Ubuntu desktop (ubuntu-8.10-desktop-i386)
The installation process complete without any warning or error. However, after first reboot this display (I can't capture the screen, so I try to write it down to paper and retype here, may missing some info (?), sorry about that)
======================================================================
Booting 'Ubuntu 8.10, kernel 2.6.27-7.generic'

Filesystem type is ntfs, partition type 0x07
The current working directory (i.e., the relative path) is /ubuntu/disks
[Linux-bzlmage, setup=0x3000, size=0x220cb0]
[Linux-initrd @ 0x7f6c3000, 0x80c7?2 bytes]

Loading, please wait...

Gave up waiting for root device. common problem
- Boot args (cat /proc/cmdline)
   - Check root delay (did the system wait long enough?)
   - Check root (did the system wait for the right device?)
- Missing modules (cat /proc/modules ls /dev)

ALERT /dev/disk/by-uuid/7AD4FE4ID4FDFEE7 does not exist. Dropping to a shell!

BusyBox v1.10.2 ....

(initramfs) _
======================================================================
If I typed "exit;" and press enter, the boot up process continues. 
"Reading file needed ..."
The only thing look abnormal is a line show up a bit after that:
502.089209 ck804xram ...  Unable to register resource 0x000 ... _ kernel bug? (I can't catch that all, it still run through this)
And after a while, ubuntu gui show up as normal.

---

### Post by ago on 2008-10-31
please post the output of

cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions
grep err /casper.log -A2 -B2
grep mount /casper.log -A2 -B2

---

### Post by Galzo on 2008-11-09
Thanks for response, I almost think this is forgot. Here is the result, two last command doesn't return anything helpful (grep: /casper.log: No such file or directory - I'm doing anything wrong?)

cat /proc/cmdline
root=UUID=7AD4FE41D4FDFEE7 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 

cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=755 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/sdc1 /host fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/loop0 / ext3 rw,errors=remount-ro,data=ordered 0 0
/dev/loop0 /dev/.static/dev ext3 ro,errors=remount-ro,data=ordered 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
varrun /var/run tmpfs rw,nosuid,mode=755 0 0
varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
/dev/sdc1 /boot fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
gvfs-fuse-daemon /home/ikantos/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user_id=1000,group_id=1000 0 0
/dev/sdb1 /media/FreeAgent\040Drive fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0

cat /proc/partitions
major minor  #blocks  name

   8     0  312571224 sda
   8     1   73407568 sda1
   8     2          1 sda2
   8     5  239160568 sda5
   8    16  732574584 sdb
   8    17  732572001 sdb1
   8    32   78184008 sdc
   8    33   78180291 sdc1
   7     0   13671875 loop0

Thanks,

Edit: Those line is after I enter GUI of Ubuntu, do I need to run these commands when stop at BusyBox?

---

