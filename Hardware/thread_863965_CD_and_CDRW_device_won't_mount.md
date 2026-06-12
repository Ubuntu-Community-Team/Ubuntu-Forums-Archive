---
title: "CD and CDRW device won't mount"
date: 2008-07-19
forum: Hardware
---

### Post by badaveil on 2008-07-19
Last week everything was fine, I could even burn a cd and retrieve a document from a cd in my cd driver. The past 2 days it won't mount. My fstab reads below:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3900efb2-ac80-454e-9c35-ae791f1545a5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a4956f13-73e4-48c9-8a38-255d703c2aae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# second hdisk
/dev/sdb1	/media/disk	ext3	defaults	0	2

I even tried to insert a CD in the cd as well as the CDRW device in the hope that it would auto-mount but got no reaction at all.
Any advise?

---

### Post by badaveil on 2008-07-20
What luck! There was actually nothing wrong with both my computer. I didn't realize that the CD given by my friend WASN'T in fact a CD but a DVD and both my devices are a CD and CDRW reader.

No wonder the devices didn't read the DVD.#%@&!!!!

---

