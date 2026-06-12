---
title: "Problem with disk check"
date: 2008-08-29
forum: Hardware
---

### Post by Hrafnkell on 2008-08-29
Hello everyone.

I haven't been able to find a solution to my problem in this forum so I wanted to see if anyone could help me with this

I have an external usb2 hard drive ( /dev/sdb1 )formatted in ext3. Every time I start the computer I get this error message:

  Log of fsck -C3 -R -A -a 
  Sat Aug 30 00:43:09 2008

  fsck 1.40.8 (13-Mar-2008)
  fsck.ext3: Unable to resolve 'UUID=5925e1ce-6cd9-4b36-83dd-f01885998171'

  fsck died with exit status 8

I press control D and every thing is fine. Ubuntu starts, I can mount the drive and access everything, but it is a little bit annoying and I'm worried as to if this proves to be more of a problem.

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa744fa2-63b7-48f4-80d8-61b991894e14 /               ext3    defaults,errors=remount-ro 0       1
#/dev/sdb1
UUID=5925e1ce-6cd9-4b36-83dd-f01885998171 /media/disk ext3 defaults 0 2
# /dev/sda5
UUID=b32c9042-246a-4e3b-979a-950144cfb3e3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

If anyone could please tell me what I need to do I would be most grateful:-)

---

