---
title: "Second Hard Drive Not Accessible"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by nutsobilly on 2006-01-21
I recently installed Ubuntu on a old 450Mhz Gateway.  This PC has 2 hard drives...a 40GB (primary) and a 13GB.  I have them both showing on the Disk Manager...but I cannot view or browse to the space on the 13GB Drive.  In the Disk Manager it says that the drive is "Inaccessible".

Access Path: none
File System: ext3
Drive Name: /etc/hda5 (Partitioned #5 at install)

What do I have to do to get this hard drive space to be accessible and usable in my file system?  PS - I'm using Linux as a file server for my Windows XP files...so far so good with Samba on the 40GB drive.

---

### Post by JAwuku on 2006-01-21
Should the drive designation not be **/dev/hda5** instead of **/etc/hda5**? Please post a listing of your **/etc/fstab** file. What file system is the 13GB drive formatted as?

---

### Post by nutsobilly on 2006-01-22
Sorry...

The config is /dev/hda5

File system is Extended 3.

---

### Post by nutsobilly on 2006-01-22
Goal - Make HDB5 available as a resource to my Windows machine...help!

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hdb5       none            swap    sw              0       0**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.0.1/linux /media/hda smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777
0	0

---

### Post by MJN on 2006-01-22
/dev/hdb5 is your swap partition.

What exactly is it you're trying to do here?! ;) 

Mathew

---

### Post by JAwuku on 2006-01-22
Hi Billy,

From your /etc/fstab file it seems that the /dev/hdb5 partition is being used as a swap partition, used by Linux as a buffer for memory. I don't think you would be able to get any info from that.

However, as you earlier stated, if your 13GB disk is located in /dev/hda5, you can let Linux recognize it by first making a new directory if it does not already exist:

```
sudo mkdir /media/hda5
```

then adding the line to your **/etc/fstab**

```
/dev/hda5       /media/hda5          ext3 defaults
```

and the /dev/hda5 partition should be recognized when you reboot. Just **cd /media/hda5** to access it.

Hope this helps,

Jason

---

