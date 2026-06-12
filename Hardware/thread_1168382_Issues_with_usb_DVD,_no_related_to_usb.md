---
title: "Issues with usb DVD, no related to usb"
date: 2009-05-24
forum: Hardware
---

### Post by Lostin60's on 2009-05-24
I am having an issue with my usb dvd drive.  It  is not being recognized by the system.  It's not a usb issue, as the usb port i am using is good. And my pos external dvd drive is fine. I am guessing that the values in /etc/fstab may be the culprit, so  I tried this. I changed 

```
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` to
```
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom0  auto    rw,user,noauto,exec,utf8 0       0
``` as there are the only /cdrom and /floppy folders in /media. I rebooted.  Still no drive.  So I ran
```
daniel@mypos:/$ sudo mount /dev/scd1 /media/cdrom0
mount: special device /dev/scd1 does not exist
daniel@mypos:/$ 
```

I tried a couple other configurations of /dev/* and /media/* to no avail.  At which point I returned everything to normal, and posted.  I am stuck.  Any and all help will be appreciated.  Below is my info.

```
daniel@mypos:/$ls /dev
```  
returns dsp
        [COLOR="White"]aaaaaaa[/COLOR]dvd                                           
        [COLOR="White"]aaaaaaa[/COLOR]dvdrw                                           
```
ls /dev/scd*
``` returns /dev/scd0 
===========================================    
Below are files and folders from my /dev folder.

Name: scd0
Type: link to block device (inode/blockdevice}
Link target: sr0 
Contents: 0 bytes (0 bytes)    "file"

Name: dvd
Type: link to block device (inode/blockdevice}
Link target: sr0 
Contents: 0 bytes (0 bytes)    "file"

Name: dvdrw
Type: link to block device (inode/blockdevice}
Link target: sr0 
Contents: 0 bytes (0 bytes)    "file"

Name: cdrom
Type: link to block device (inode/blockdevice}
Link target: sr0 
Contents: 0 bytes (0 bytes)    "file"

Name: cdrw
Type: link to block device (inode/blockdevice}
Link target: sr0 
Contents: 0 bytes (0 bytes)    "file"

==================================================
Below are files and folders from my /media folder.

Name: cdrom
Type: Link to folder (inode/directory)
Link target: cdrom0
Contents: nothing             "folder"

Name: cdrom0
Type: Link to folder (inode/directory)
Link target: cdrom0
Contents: nothing              "folder"

Name: cdrom1
Type: folder (inode/directory)
Link target: 
Contents: nothing              "folder"

Name: floppy
Type: Link to folder (inode/directory)
Link target: floppy)
Contents: nothing              "folder"

Name: floppy0
Type: folder (inode/directory)
Link target: 
Contents: nothing              "folder"

===========================
Below is my /etc/fstab file
 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=165586ed-0484-4189-877f-10307fde890a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fdec8c64-23a5-4ce9-8bc4-bc7ce2f9b0b7 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0

[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-05-26
Hmmm, someone answered this post, but his reply seems to have disappeared. So, the previous post lists my issues.  Here is my original fstab file.
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=165586ed-0484-4189-877f-10307fde890a / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=fdec8c64-23a5-4ce9-8bc4-bc7ce2f9b0b7 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/floppy0 auto rw,user,noauto,exec,utf8 0

 
```

Here is my fstab file as it is now.  I chopped off some of the top to fit in one screenshot.
```
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=165586ed-0484-4189-877f-10307fde890a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fdec8c64-23a5-4ce9-8bc4-bc7ce2f9b0b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrw0  auto    rw,user,noauto,exec,utf8 0       0
```

I also tried
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrw1  auto    rw,user,noauto,exec,utf8 0       0
``` I have a basic understanding of the problem, but I don't how to fix it.  As always, any help will be appreciated.

[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-05-28
Solved

---

