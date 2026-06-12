---
title: "Inaccessable USB and lost of data - file bigger than the device"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by roschell on 2007-09-27
What happened is that backup copy of partition was made on wrong drive. USB with valuable data was possibly overwritten with the backup. 

The 'dd' command was used as follows 'dd if=/dev/sda6 of=/dev/sdb1 conv=noerror'

Now there is a problem with accessing the usb. It is found by the system and replying:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,     missing codepage or other error     In some cases useful info is found in syslog - try     dmesg | tail or so

after visiting syslog I found this:

ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
ReiserFS: sdb1: warning: Filesystem on sdb1 cannot be mounted because it is bigger than the device
ReiserFS: sdb1: warning: You may need to run fsck or increase size of your LVM partition
ReiserFS: sdb1: warning: Or may be you forgot to reboot after fdisk when it told you to

What could I do to find and retrieve the original data from the USB, if possible.

Thanks

---

