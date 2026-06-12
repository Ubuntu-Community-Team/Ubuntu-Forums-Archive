---
title: "cannot delete some folders on external drive"
date: 2010-07-04
forum: Hardware
---

### Post by noworldorder on 2010-07-04
Ubuntu 10.04

I am unable to delete some folder on an external hard drive.  In windows I can delete all files on this external hard drive.  I cannot see what is different about the particular folders I am unable to delete in Ubuntu.

thanks - chris

---

### Post by Jeroensum on 2010-07-04
The disk maybe mounted read-only or with rights to a specific user.
Can you fire up a terminal and tell me what *mount* returns when the disk is plugged in?

---

### Post by noworldorder on 2010-07-04
> Can you fire up a terminal and tell me what *mount* returns when  the disk is plugged in?

Oooo...   sounds good but I am 110% noobie.  Can you walk me throught this?  Thanks - Chris

---

### Post by efflandt on 2010-07-05
Open a terminal (Applications > Accessories > Terminal)
You may want to make it wide by selecting 132x24 from Terminal menu, then type: **mount** (and hit enter key)

You can use the mouse to highlight that output and right click to copy, then paste it to a message.

---

### Post by noworldorder on 2010-07-05
thanks - this is what I got:

chris@chris-laptop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/bichris@chris-laptop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
//192.168.1.105/MediaShare on /mnt/MediaShare type cifs (rw,mand)
//192.168.1.105/Backup on /mnt/Backup type cifs (rw,mand)
nfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
//192.168.1.105/MediaShare on /mnt/MediaShare type cifs (rw,mand)
//192.168.1.105/Backup on /mnt/Backup type cifs (rw,mand)

---

