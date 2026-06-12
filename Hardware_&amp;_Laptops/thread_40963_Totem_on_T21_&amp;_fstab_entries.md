---
title: "Totem on T21 &amp; fstab entries"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by JulesH on 2005-06-11
Hi,

When I try to use Totem on my T21 to play DVD's, I get the folllowing message:

"Failed to find mountpoint for device /dev/hdd in etc/fstab".

Looking in fstab, there is no entry for the CD-RW/DVD-ROM I am using for playing DVD's etc. but there is an entry for a CD-ROM drive, (which Ubuntu was installed from), which I use for booting from CD (the CD-RW/DVD-ROM is not bootable on my machine).

How do I add the correct entries for this drive?


My fstab currently looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

The drive I want to add is a Sony CD/RW/DVD-ROM type CRX820E.

I tried to add a new entry:

/dev/hdd        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0

or:

/dev/hdc        /media/cdrom1   udf,iso9660 rw,user,noauto  0       0

Neither work, and I get the following error message when I try to play a DVD: "Error 8192".

What's up?

Regards,
Jules

---

