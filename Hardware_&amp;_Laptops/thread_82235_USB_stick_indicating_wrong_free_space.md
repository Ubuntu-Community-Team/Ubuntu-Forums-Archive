---
title: "USB stick indicating wrong free space"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by lomos on 2005-10-26
I got a stick from my friend, he copied some files on a windows machine onto it.

I wanted to delete files and use the free space for some other stuff, but after deleting the free space remains the same as before. I cannot use it at all...

any suggestions?

dmesg output:
[4303969.394000] SCSI device sdb: 501760 512-byte hdwr sectors (257 MB)
[4303969.395000] sdb: Write Protect is off
[4303969.395000] sdb: Mode Sense: 23 00 00 00
[4303969.395000] sdb: assuming drive cache: write through
[4303969.395000]  /dev/scsi/host7/bus0/target0/lun0: p1
[4303969.397000] Attached scsi removable disk sdb at scsi7, channel 0, id 0, lun 0
[4303969.399000] usb-storage: device scan complete
[4303969.984000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


cheers,
Thomas

---

### Post by lomos on 2005-10-26
solved, ubuntu created a .Trash directory, and moved everything into it...

:?

---

### Post by irishwhite on 2008-02-09
i had the same problem and so i took my usb drive to my windows computer and saw the .trash folders.  well, i knew i didn't want them there so i deleted them while connected to the windows computer, and now when i plug the usb drive into my ubuntu computer, it still shows that i have next to no free space, when i should have well over 3 gigs free.  am i screwed because i deleted the .trash folders on my windows box?

---

