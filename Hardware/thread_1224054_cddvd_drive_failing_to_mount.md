---
title: "cd/dvd drive failing to mount"
date: 2009-07-26
forum: Hardware
---

### Post by ShortE on 2009-07-26
Hi All!  Currently, my dvd drive won't recognize when I put a cd in, and when I try to force it to mount it says there is no media in the drive.  I found some suggestions on what to poke via the terminal to figure out what's wrong, so I tried some of them, but I really don't know how to interpret the data.  I've pasted that below.  This all started when I was trying to make ubuntu run restricted dvds and I installed a bunch of stuff via the command line (which probably was a mistake given my lack of experience).  I've also noticed people referring to "media" as if it is a folder or location in my home folder where all might be revealed, but I can't find anything called media in any of the pulldown menus:confused:.  Any insight would be awesome!

abbi@CharlieII:~$ sudo mount
[sudo] password for abbi: 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/abbi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=abbi)
abbi@CharlieII:~$ sudo mount /dev/cdrom
mount: no medium found on /dev/sr0
abbi@CharlieII:~$ sudo mount /dev/scd1
mount: can't find /dev/scd1 in /etc/fstab or /etc/mtab
abbi@CharlieII:~$ sudo mount /dev/dvd
mount: no medium found on /dev/sr0
abbi@CharlieII:~$ cat /etc/fstab /etc/mtab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6870adf2-4dcf-48e3-9f86-4f3d48145fe1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ab49764e-c8ec-453d-be67-bf4fba1f4eda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/abbi/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=abbi 0 0
abbi@CharlieII:~$ sudo mount /media/cdrom
mount: no medium found on /dev/sr0
abbi@CharlieII:~$ 
abbi@CharlieII:~$ chkdsk /f
bash: chkdsk: command not found
abbi@CharlieII:~$

---

