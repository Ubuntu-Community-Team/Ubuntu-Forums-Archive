---
title: "cd rom drive not mounting"
date: 2010-04-20
forum: Hardware
---

### Post by srswinde on 2010-04-20
Hello,

Installed Jaunty a week ago or so and everything worked fine until a few days ago the cd rom stopped getting mounted on boot up and I have been unable to mount it manually. 
I can't find the cd rom in /dev/

fstab says:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a9cd5cc9-e5ac-4858-a32f-ad61b2166417 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8b8b92dc-8e6d-4a0c-b397-e75c13bcc5b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```sudo blkid just gives the hard drive and the swap space.

The cd drive is a cd rw/dvd. It came With the IBM thinkpad

Any Suggestions would be greatly appreciated

---

### Post by garvinrick4 on 2010-04-20
> **srswinde said:**
> Hello,

Installed Jaunty a week ago or so and everything worked fine until a few days ago the cd rom stopped getting mounted on boot up and I have been unable to mount it manually. 
I can't find the cd rom in /dev/

fstab says:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a9cd5cc9-e5ac-4858-a32f-ad61b2166417 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8b8b92dc-8e6d-4a0c-b397-e75c13bcc5b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```sudo blkid just gives the hard drive and the swap space.

The cd drive is a cd rw/dvd. It came With the IBM thinkpad

Any Suggestions would be greatly appreciated Copy and paste these.

sudo mkdir /media/cdrom0

sudo mount /dev/scd0 /media/cdrom0

sudo umount /media/cdrom0

---

### Post by srswinde on 2010-04-21
> 
Copy and paste these.

sudo mkdir /media/cdrom0

sudo mount /dev/scd0 /media/cdrom0

sudo umount /media/cdrom0

Unfortunately there is no scd0 in /dev/. Thats why it doesn't mount on boot, it is written in the fstab file as scd0. Perhaps it would be called something else? 
I know the cd drive works because I can boot from it.

---

