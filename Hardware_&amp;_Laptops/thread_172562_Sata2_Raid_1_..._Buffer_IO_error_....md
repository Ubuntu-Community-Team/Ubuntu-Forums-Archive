---
title: "Sata2 Raid 1 ... Buffer I/O error ..."
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by Oshaka on 2006-05-08
Hello all,


Just got my new server, put 2 WD2500YD's in raid1 and started to copy information from my pci-to-ide card's HDs to my new SATA drives... 

But half way though I get these dreaful errors

"148.521240] Buffer I/O Error on device sda1, logical block 11278197
....
....
ata5: command 0x35 timeout, stat 0xd1 host_stat 0x61
ata5: translated ata stat/err 0x35/00 to SCSI SK/ASC/ASCQ 0x4/00/00
...
"


What do they mean, and what is wrong with my box?

---

### Post by Oshaka on 2006-05-08
edit: ignore the reply. still need help with primary post

---

### Post by JCorrea920 on 2006-05-09
Try this [http://www.humandoing.net/blog/33/raid-on-linux-ubuntu-510]("http://www.humandoing.net/blog/33/raid-on-linux-ubuntu-510")

Let me know if this helps. I want to  try something similar with two SATA hard drives but need to know if it works before I start.

Jorge

---

