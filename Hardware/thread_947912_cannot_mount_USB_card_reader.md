---
title: "cannot mount USB card reader"
date: 2008-10-14
forum: Hardware
---

### Post by brucedixon on 2008-10-14
I edited the fstab file by hand trying to get it to mount a usb hard drive I have formatted with NTFS.  Now I can't mount my digital camera or my usb flash card reader, nor the NTFS drive.

The card reader shows up in "places" but the message is "cannot mount volume - you are not privileged to mount this volume".  So I guess the question is what do I do to get access to my digital camera and card reader, and maybe even the ntfs drive.  

This is what my fstab file looks like right now

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f705b354-21db-4ef0-8143-33ca51a23eba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f9327851-4a2a-41ce-b7e0-fecc7a0b55b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/media/yemaya	ntfs-3g force	0	0
/dev/usb	/media/sub	fat	user	noauto

Any advice is deeply appreciated, both by me and the grandchildren who expect:confused: me to print their pictures.

bd

---

