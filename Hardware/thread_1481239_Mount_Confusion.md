---
title: "Mount Confusion"
date: 2010-05-12
forum: Hardware
---

### Post by tigerglebe on 2010-05-12
Ubuntu 10.04

/dev/sdb1 refuses to mount.  Under Disk Utility it shows as unmounted.  If you try to mount it it says it's already mounted.  Dolphin gives the error: 'An error occured while accessing '320g', the system responded: mount: according to mtab, /dev/sdb1 is already mounted on / mount failed.'

```

 cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e0394ad6-4b4a-47d1-99a0-b6faf741ef2a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
uncle@uncle-desktop:~/Documents$ 
```

Any suggestions please?

---

### Post by mikewhatever on 2010-05-12
You should post the output of **mount** to see what's going on. Many times a partition would not get mounted, because it is marked unclean, and all you need to do is run a file system check.

---

### Post by tigerglebe on 2010-05-12
BTW,  mtab shows this:

```
cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/uncle/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=uncle 0 0
```

and mount shows:
```

mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
gvfs-fuse-daemon on /home/uncle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=uncle)

```

---

### Post by tigerglebe on 2010-05-12
```
fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdb1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

```

I need to get it to show as unmounted so I can check it and remount.  How do I do this?

Gets better:

```

umount /dev/sdb1
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

---

### Post by tigerglebe on 2010-05-12
> **mikewhatever said:**
> You should post the output of **mount** to see what's going on. Many times a partition would not get mounted, because it is marked unclean, and all you need to do is run a file system check.

Done, see above :-)

---

### Post by dino99 on 2010-05-12
sudo shutdown -F -r now (will force a fsck on next reboot)

but you can install mountmanager to tweak your devices and partitions preferences

---

### Post by tigerglebe on 2010-05-12
> **dino99 said:**
> sudo shutdown -F -r now (will force a fsck on next reboot)

but you can install mountmanager to tweak your devices and partitions preferences

mountmanager did it.  thanks

---

### Post by tigerglebe on 2010-05-12
Looks like I spoke too soon.  I can't access it.  On top of it I suddenly can't access anything unless I reboot.  I get the message Permission Denied even under Terminal under root.  It'll apply to everything on the computer until I reboot.  From Firefox to apps launched from the Terminal.

---

