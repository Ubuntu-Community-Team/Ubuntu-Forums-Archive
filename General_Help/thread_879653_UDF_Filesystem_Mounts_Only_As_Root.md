---
title: "UDF Filesystem Mounts Only As Root"
date: 2008-08-04
forum: General Help
---

### Post by H4rm0ny on 2008-08-04
Hi,

I have a Lite-On Blue-Ray / HD drive that works fine. In order to mount HD and Blue-Ray discs, I compiled and installed my own udf.ko module (using the instructions *_[here]("http://ubuntuforums.org/showthread.php?t=718744")_*).

I can mount the drive successfully, either through Dolphin or from the command line, but the mounted directory becomes accessible *only* to root.

I suspect that this has something to do with it being UDF because I have even ripped an iso a HD disc and mounted that! And guess what - it was accessible only by root.

I've tried various mount commands. My fstab is as follows:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=63d5dab8-0cd4-419d-986b-42c94fe21169 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda3
UUID=fffec921-077f-45c2-af08-85ec37a3c544 /home ext3 nouser,relatime,atime,auto,rw,dev,noexec,suid 0 2
# /dev/sda1
UUID=a5df0c68-fa22-4ad3-bcf4-ea0fe1cd3694 /srv ext3 nouser,relatime,atime,auto,rw,dev,noexec,suid 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
#NAS
sshfs=aurum@192.168.200.3:/    /media/honeypot    fuse    defaults    0 0
#aurum@192.168.200.3/shares/internal
/dev/sdb2 /mnt/storage_disk auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0

```

Doesn't seem to matter where I mount this or as which user. Everything is fine with regular DVDs.

My system is a kubuntu Hardy Heron install, all up to date.

Any suggestions greatly appreciated. Can check anything you need me to check.

Thanks,

Harmony.

---

### Post by H4rm0ny on 2008-08-05
Okay, it definitely appears to be a problem with mounting UDF file systems. I've re-created UDF discs just as isos and no matter what the permissions are set to in the mount command, they remain accessible only by root.

I have successfully copied the *contents* of discs onto my hard drives and I can work with them from there. But at 25+ GB per disc, that eats up space pretty fast and takes a lot of unnecessary time copying.

Anyone?

-H.

---

