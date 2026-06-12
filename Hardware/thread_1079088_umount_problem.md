---
title: "umount problem"
date: 2009-02-24
forum: Hardware
---

### Post by tdashroy on 2009-02-24
Okay so I haven't had this problem 'till today. I reformatted this usb flash drive and renamed it, and now I am unable to unmount it with the command

```
umount /media/school_drive
```

Whenever I run this command I get the following error

```
umount: /media/school_drive is not in the fstab (and you are not root)
```

Can someone explain to me what it means by it is not in the fstab? I have never had any trouble with this before and I don't remember changing anything in the fstab. The commands I used to reformat and rename my drive were

```
sudo fdisk /dev/sdg
sudo mkfs.ntfs /dev/sdg1
sudo ntfslabel /dev/sdg1 school_drive 
```

Here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b3b0d97f-8761-4bb8-93b3-d213b015c38d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any help or suggestions as to how I can get this back to normal would be much appreciated. Thanks

-Troy

---

### Post by x33a on 2009-02-24
try unmounting it with sudo.

alternatively, when it's mounted find out the device name with "df", something like sda,sdb,etc..

then, sudo umount /dev/sdb (assuming sdb is the flash drive).

---

### Post by tdashroy on 2009-02-24
Thanks for the reply, and yea it works with sudo, but I was wondering how I could get it back to where I didn't have to use sudo. I was also wondering what I did to cause this.

---

### Post by x33a on 2009-02-24
maybe this can help.

[http://wiki.ubuntu.org.cn/UbuntuHelp:UsbFlashDrives](http://wiki.ubuntu.org.cn/UbuntuHelp:UsbFlashDrives)

if you manually mount the drive, i think it cannot be unmounted without sudo.

---

### Post by tdashroy on 2009-02-24
Alright cool, that wiki helped me out. I ended up just reformatting it to be FAT32 instead of NTFS, and the wiki redirected me to one where that helped me rename the drive, which was my ultimae goal in the first place! Thank you much!

---

