---
title: "Unable to write to NTFS external drive"
date: 2008-09-03
forum: Hardware
---

### Post by jordan28 on 2008-09-03
Hello,

I am trying to use my Maxtor 80GB ntfs external hard drive to backup personal files. It was partitioned in the store on a Windows PC. When I insert the USB cable, the drives are automatically mounted and appear through the GUI in my /media. I am unable to write to the drives. Here are the fdisk, fstab, mtab  files:

--------------------------------------------------
[INDENT]jordan@dell:~$ fdisk -l

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9729    37190475    7  HPFS/NTFS[/INDENT]
--------------------------------------------------

[INDENT]jordan@dell:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f92f34a9-cc78-4a19-8fbf-987221fbf987 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ca0f0d10-6ae2-47c2-a217-cb31bd84d245 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=d7e4b06c-c74f-4ca3-a07e-497aac4523cd  /boot ext3 defaults 0 0
[/INDENT]
---------------------------------------------------

[INDENT]jordan@dell:~$ cat /etc/mtab
/dev/sda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda3 /boot ext3 rw 0 0
tmpfs /lib/modules/2.6.20-16-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb2 /media/New\040Volume___ ntfs rw,nosuid,nodev,umask=222,utf8 0 0
/dev/sdb1 /media/New\040Volume____ ntfs rw,nosuid,nodev,umask=222,utf8 0 0
[/INDENT]
--------------------------------------------------

It seems that I have the rw privileges, but I still can't write. I have also installed the program ntfsprogs, but I'm not sure if that should help, or exactly what I need to edit. I have worked at some of the solutions proposed in other similar threads without success. I appreciate any help in this situation!

---

### Post by JK21 on 2008-09-03
Hi,

 have you tried this??

NTFS Configuration Tool
Enable/disable write support for any NTFS devices  
This program allows you to easily configure all of your NTFS devices to allow write support via a friendly gui. For that use, it will configure them to use the open source ntfs-3g driver. You'll also be able to easily disable this feature.
Homepage : [http://givre.cabspace.com/ntfs-config](http://givre.cabspace.com/ntfs-config)
Homepage of ntfs-3g : [http://www.ntfs-3g.org](http://www.ntfs-3g.org)

---

### Post by jordan28 on 2008-09-03
That worked great. I even already the program installed, just didn't know I needed that one line of code. Thank you JK21!

---

### Post by jordan28 on 2008-09-03
Actually, I may have made a mistake. I just mounted it to my /media drive and I think it wrote over the other contents of the that file, namely my Cdrom0. Can I remount my cdrom or unmount the external drive contents?

Thanks for your help though, I should have originally mounted to a sub-folder.

---

