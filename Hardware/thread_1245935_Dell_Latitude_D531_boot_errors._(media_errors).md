---
title: "Dell Latitude D531 boot errors. (media errors)"
date: 2009-08-21
forum: Hardware
---

### Post by Haarlem on 2009-08-21
Hi and greetz from The Netherlands,
 
I have poked around in [linux]("http://www.linuxforums.org/forum/#") off and on for years, but am still a total n00b.
 
One of the things I havn't been able to get fixed are the MANY errors I encounter during the boot. Buffer i/o errors, media errors etc. Though at the end of the rain of errors, I do get a prompt, I can start my GUI and the things I use seem fine. The video, the sound, my network interfaces, USB...
Seeing as how the errors take aprox. 3minutes, I would love to get rid of them and boot nice and clean and quickly.
 
I use: Kubuntu 9.04. MD5 checked OK. CD verified OK.
 
I made a video showing the boot containing many errors (sorry for the quality):Youtube.com search code: NuvpnDdPiuk.
 
All advise and or tips in the right direction will be greatly appreciated!

PS. Previous assistance brought me this extra info:

Mount:
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
 
Fdisk:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5267    42307146    7  HPFS/NTFS
/dev/sda2            5268        9729    35841015    5  Extended
/dev/sda5            5268        9540    34322841   83  Linux
/dev/sda6            9541        9729     1518111   82  Linux swap / Solaris

Here is the result of the fsck ran from Kubuntu Live CD:
 
ubuntu@ubuntu:~$ sudo fsck.ext3 -fcky /dev/sda5
e2fsck 1.41.4 (27-Jan-2009)
Checking for bad blocks (read-only test): done
/dev/sda5: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
 
/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 116084/2146304 files (0.6% non-contiguous), 1449724/8580710 blocks
 
After this I rebooted from HDD and the errors are still there, in abundance.
 
If at all it is any help analytically, the same errors occur while not only booting Kubuntu from fresh install on HDD (after md5check and CD intergrity chaeck) but, also when booting from Kubuntu Live CD and Backtrack 4 pre-release Live USB.

---

