---
title: "HP Mini 311 won't boot"
date: 2010-10-29
forum: Hardware
---

### Post by cmmichael on 2010-10-29
This seems to be a common hardware problem with these models, I haven't been able to find a solution yet. I am trying a new install of 10.04 desktop on a mini 311 with a new hard drive, no windows. It boots fine from the pendrive, but will not boot from the HD, just a blinking cursor on a black screen. 

I am on a public computer now, so I can run diagnostics and post tomorrow. It seems that tweaking the files on the pendrive and reinstalling might do it. I just need to know what diagnostics to run.

---

### Post by cmmichael on 2010-10-29
Here is some info:

HP Mini 311 - 1000
Bios Revision  F.02
Processor  Intel Atom CPU N270 2 1.60 MHz
Total Memory 1024 MB
WLAN FCC ID  QDS-BRCM1030

ubuntu@ubuntu:~$ cat /etc/fstab 
aufs / aufs rw 0 0 
tmpfs /tmp tmpfs nosuid,nodev 0 0 
/dev/sda5 swap swap defaults 0 0 
ubuntu@ubuntu:~$ cat /proc/mounts 
rootfs / rootfs rw 0 0 
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0 
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0 
none /dev devtmpfs rw,relatime,size=442660k,nr_inodes=110665,mode=755 0 0 
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0 
/dev/sdb1 /cdrom vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0 
/dev/loop0 /rofs squashfs ro,noatime 0 0 
tmpfs /cow tmpfs rw,noatime,mode=755 0 0 
aufs / aufs rw,noatime,si=49efa87e 0 0 
none /sys/fs/fuse/connections fusectl rw,relatime 0 0 
none /sys/kernel/debug debugfs rw,relatime 0 0 
none /sys/kernel/security securityfs rw,relatime 0 0 
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0 
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0 
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0 
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0 
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0 
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0 
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0 
ubuntu@ubuntu:~$  lspci | grep VGA 
02:00.0 VGA compatible controller: nVidia Corporation C79 [Quadro FX 470M] (rev b1)

---

