---
title: "Impossible to mount external HD in ubuntu 8.10"
date: 2008-11-05
forum: Hardware
---

### Post by zamot.de on 2008-11-05
Sorry if I open a new thread similar to others frequently possible to find in the web, but I didn't find any solution yet.

Relevant informations about Hardware: I have a laptop LG LW20 Express
The HD in question is a TVIX (Dvico Digital Jukebox 3100U) in NTFS partition.In my Ubuntu distro it is recognized as sdb1 and the label is TVIX

6 months ago I changed from windows (could not stand anymore) to Linux.
Tried several distro but all gave me lot's of problems (the only common to all was 'no sound' and no 'sd card reading'). My final option was PCLINUXOS and my external HD TVIX always worked fine with it. But my laptop was always overeating with PCLINUXOS (and no sound was not anymore possible to accept) so I decided to change to the new ubuntu. I did put all my personal files in my TVIX and install ubuntu.
The problem is that now I can't access the disk. All works fine (less sound and shutdown and SD card and webcam, but I hope there will be a solution for that soon so I wait) besides that. And I need to access my files urgently. I tried to open it in the computer of a friend who as windows XP and it works, I can see my files there. I then removed the disk using windows safely remove tool. COme back to ubuntu and the problem persists. The force mount command doesn't work neither.

Here are some terminal informations about it:


**root@eat:/home/eat# fdisk -l**

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

[B]
eat@eat:~$ sudo mount[/B]

[sudo] password for eat: 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eat/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eat)
/dev/sdb1 on /media/TVIX type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

**root@eat:/home/eat# mount -l**
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eat/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eat)

This last one seems not finish since the path root@eat doesn't became visible and I have to close the terminal window.

Please help me
and thanks

---

