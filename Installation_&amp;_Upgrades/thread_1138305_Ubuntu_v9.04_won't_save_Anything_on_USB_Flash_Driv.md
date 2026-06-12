---
title: "Ubuntu v9.04 won't save Anything on USB Flash Drive"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by corsairgt on 2009-04-26
I've installed v9.04 on a 16 GB USB flash drive. However, it wouldn't save any configuration, updates or new software. Does anyone know why?

---

### Post by Triptol on 2009-04-26
You might have set the flash to read-only (check whether you have a button with a lock/unlock symbol on the flash).

The filesystem might also be mounted read-only. Check what the "mount" command gives in a terminal.

---

### Post by corsairgt on 2009-04-26
My flash drive doesn't have a lock.

If the filesystem is mounted as read-only, how do I change it to read and write. I never had this problem when I was using v8.04.

---

### Post by linux_tech on 2009-04-26
Try running a check of the drive ie
First check to see what the media is assigned 

```
sudo fdisk -l
``` (lowercase L)
if it is assigned /dev/sdb1, then try this command:
```

sudo dosfsck -a /dev/sdb1


```

then test flash again


[https://help.ubuntu.com/community/Mount/USB#Device%20become%20suddenly%20read%20only](https://help.ubuntu.com/community/Mount/USB#Device%20become%20suddenly%20read%20only)

[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)

---

### Post by corsairgt on 2009-04-26
> **Triptol said:**
> You might have set the flash to read-only (check whether you have a button with a lock/unlock symbol on the flash).

The filesystem might also be mounted read-only. Check what the "mount" command gives in a terminal.

Results:-

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sdb1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$

What do I need to do next?

---

### Post by Triptol on 2009-04-27
Hmmmm... kinda funny. What started your boot, seems to me you are running from a ramdisk (your / is mounted as rootfs). Seems things weren't really installed on your disk. 

But I'm not quiet sure.

I would guess your flashdrive is identified as /dev/sda.

what happens if you execute the following:
```

mkdir /tmp/sda1
sudo mount /dev/sda1 /tmp/sda1
ls /tmp/sda1
```
Do you see a root filesystem (with bin, etc, usr, etc...)?

---

