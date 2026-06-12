---
title: "UsbDisk Problems.. ( Read-Only )"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by Juspriss on 2006-04-03
Hi @ all guys ;)
I use an usbdisk on my laptop ( with breezy ).
The premissions are on ReadyOnly and i can't take the Write & Execute.. ](*,) 

I have tryed with "chmod +rw /media/usbdisk/Folder" but it doesn't work...
can anyone tell me where i wrong please?

Thanks a lot @ all & Sorry for my bad english, Juspo ;)

---

### Post by frusch on 2006-04-03
Hi, my English is bad, too!!!

I've the same problem but in this way: when I log in the permission is rw for a while (about 10-15 min.) then it turn into r..

I can set it to rw with "chmod" but 10-15 minute later it turn into r again.

I hope that somebody will help us!!!

Thanks.

---

### Post by Juspriss on 2006-04-04
[QUOTE=frusch]Hi, my English is bad, too!!!

I've the same problem but in this way: when I log in the permission is rw for a while (about 10-15 min.) then it turn into r..

I can set it to rw with "chmod" but 10-15 minute later it turn into r again.

I hope that somebody will help us!!!

Thanks.[/QUOTE]

your english is better than mine ;)

I have a similar problem but my permission's "duty time" is about 0.. :( 
after the chmode the permissions return to readonly.. ](*,)

p.s. if i mount it in the fstab? :confused:

---

### Post by frusch on 2006-04-04
Hi here's my fstab it may help you.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/LACIE  auto    rw,user		0	0	

I can tell you that I could solve the problem. My FAT was damaged. 
I made "dosfsck" from the terminal with the disk unmounted. Try it!!!

---

