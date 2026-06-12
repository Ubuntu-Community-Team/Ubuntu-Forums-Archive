---
title: "DVDROM Won't Read Data DVD's"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by kwylez on 2007-03-29
I am able to insert a dvd movie and play it in my dvdrom.  If I insert a data cd or audio cd the DVDROM will see/play it, but if I insert a data dvd in then nothing happens.  The drive icon isn't even appearing in "my computer".  When I eject the data dvd then the icon appears again.

Below is my /etc/fstab. (the dvd rom is mounted to /media/cdrom0

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=af3c3529-1205-4ec3-bfbb-89a159d629fe /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=51464eb7-588b-4a5c-8978-6b5d0052af6b none            swap    sw
 0       0
[COLOR="Red"]/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


# Data Drive
/dev/hdb1     /mnt/data     ntfs-3g     defaults,locale=en_US.utf8   0    0

Any advice would be very helpful.

Thanks...

---

### Post by Joseph IronEagle on 2007-03-29
Have you tried the disks in another drive? I just went through this with my disks,  K3b provided the solution, the discs were DVD-r though they showed in K3b as DVD- rw ISO9660, replaced the drive, all the disks read fine in the new Liteon I bought. Just a thought.

---

### Post by kwylez on 2007-03-29
Yea I have tried the disks in another drive and they worked fine.  I am getting an external USB DVD burner tomorrow so I will see how that works out.  It just boggles my mind because Ubuntu does recognize the drive as  DVD-ROM.

---

