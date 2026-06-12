---
title: "EEE PC Can't mount internal hard drive"
date: 2008-11-11
forum: Hardware
---

### Post by Nel013 on 2008-11-11
Can anyone help me?  I purchased a ASUS EEE 1000H Laptop and did not like the install linux version.  The laptop has 2 drives in it, 8Gb and 32Gb. I first installed Ubuntu 8.04.1 on the larger drive, thus retaining the original linux on the smaller drive.  I encountered major hardware problems with the WiFi and on searching here for a solution found Ubuntu-EEE which I then installed on the smaller 8Gb drive.  I have reformatted the 32Gb drive which is now clear, but each time linux starts it does not mount the larger 32Gb drive.  I can mount it manually each time after boot up using:

 sudo mount /dev/sdb1 /media/myfat/
 sudo chmod a+rwx /media/myfat/

And it works fine I think! I have tried to include the correct line in the Fstab file, but but can't seem to get it right! The file currently looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=31fe8b8f-476b-457e-a103-e2196f395755 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4eedaca3-4e92-44cf-8eb2-1bbcd845e9d0 none            swap    sw              0       0
# /dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 	/media/myfat	vfat	defaults,umask=0000,utf8 0 0

I have commented out the last but one line so I can use USB Sticks in the laptop - another hint I found here!  But has all this affected my other hard drive?  As a help my partitions look line this:

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000110b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924    31519498+  83  Linux

As you can probably tell, I am new to this, so any help you can provide would be great!?! Thanks...

---

### Post by immerohnegott on 2008-11-11
try trimming some of the stuff off the fstab entry making it

/dev/sdb1   /media/myfat    vfat    defaults   0 0

see if you can at least get to it that way.

---

