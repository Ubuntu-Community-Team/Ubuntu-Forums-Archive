---
title: "Ubuntu Remix 10.10 and Aspire One D250"
date: 2010-11-09
forum: Hardware
---

### Post by biscoito1r on 2010-11-09
From what I could gather on the web it should have worked out of the box. Nothing happens when I connect a USB memory stick on it. It seems like the USB is not mounting.

---

### Post by biscoito1r on 2010-11-09
I get the following error when I try to mount the USB drive

> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

---

### Post by biscoito1r on 2010-11-09
here is what my /etc/mtab looks like, The USB drive is sdb1

> 
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/michelle/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=michelle 0 0

---

### Post by biscoito1r on 2010-11-09
ok, I manage to manually mount the drive, however I need to do it all the time, is there a way to fix the automounting ? The automount is already enabled on nautilus.

---

