---
title: "Permissions for External USB drive"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by moeFinley on 2007-07-28
This is mentioned alot but I've tried all the suggested solutions and nothing seems to work.  I'm trying to access a shared FAT32 external drive through SMB.  I can access other shares within my home folder but not this drive.  I know it is down to permissions so I've been editing my FSTAB which now looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0 
# /dev/hda1 -- converted during upgrade to edgy
UUID=999f3943-e36b-4496-b230-a7b2439276b3 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=acea208f-f49b-4b92-85fb-71a25f6b3e5e none swap sw 0 0 
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
# fstab mod for USB drive share
#/dev/sdd1    /media/mydrive    auto    user,rw,umask=0022    0    0
```

and MTAB looks like

```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0 
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0 
/dev/sda1 /media/mydrive vfat rw 0 0
```

But I read that FAT32 doesn't support permissions so whats the point?!  I'm guessing SMB is looking for permissions and somewhere it gets the default of no access because there are not permissions to be read?

But I know some people are sharing FAT32 drives so what's going on?  I've spent the last five hours trying to find a solution and I'm really wondering why this is so differcult.  Please help!

Thanks

---

