---
title: "DVD Drive Stopped Working, Ubuntu Doesn't Recognise"
date: 2011-07-03
forum: Hardware
---

### Post by darren123web on 2011-07-03
Hi guys,

Hopefully someone can point me in the right direction ;-)
I've spent a few hours trawling Google and the forums yesterday and today, but maybe I missed something.

I have :

[LIST]
[*]Ubuntu 10.04 LTS
[*]Dell Inspiron 530 / Quad Core / 6Gb Ram
[*]All updates as of yesterday.
[/LIST]
(My DVD drive was working perfectly until I removed it to use it in my other PC.  I think I might have done something stupid like unplug the DVD drive while the PC was still powered up.

So maybe that's the issue.)

Since then, Ubuntu doesn't recognise it.

[LIST]
[*]I've tried removing the drive, rebooting, shutting down, installing the drive repeatedly.
[*]On inserting a disk, the drive spins up briefly, but nothing shows in Places on the left hand side.
[*]I've also tried usermount program as that was suggested in another thread, but that gives me a 'proc' device listed, and I'm only able to use the Close button, the other 2 are greyed out.
[*]I've tried sudo mount /media/cdrom (and cdrom0, cdrom1) but no change
[/LIST]
Is there another command I could try?

Still a bit new to Ubuntu, so please feel free to explain anything as if you were addressing your 2 year old child !  ;-)

I've included the fstab & mtab below, in case that is of any help.

Thanks in advance, 
Darren

My mtab:

```
/dev/sda1 / ext4 rw,errors=remount-ro,user_xattr 0 0
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
gvfs-fuse-daemon /home/darren/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=darren 0 0

```

My fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b5f233da-94d0-4d6b-8eb8-b89fb62e6dfc /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=9eae7513-c3df-4480-917d-a4ea248c83cf none            swap    sw              0       0
```

---

