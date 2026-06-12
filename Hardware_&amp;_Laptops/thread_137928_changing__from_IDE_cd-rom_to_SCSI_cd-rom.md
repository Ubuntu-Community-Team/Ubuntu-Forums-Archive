---
title: "changing  from IDE cd-rom to SCSI cd-rom"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by jamesr on 2006-02-28
I am working a server version. The system was installed using an IDE CD-ROM drive but I then changed the CD-ROM to SCSI type.

I do not see the CD-ROM with

sudo fdisk -l

shows all the other drives both SCSI and IDE.

I can boot from the CD-ROM  drive , both my original installation disk and a rescue disk.

dmesg |grep scsi
scsi0:Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER Rev 6.236
scsi0:A:0:0 Tagged Queuing Enabled Depth 8
scsi0:A:0 10000 MB/S transfer (10.000 MHz, offset 15)
scsi0:A:4 10000 MB/S transfer (10.000 MHz, offset 8)
/dev/scsi/host0/bus0/target0/lun0 p1 p2 < p5 >
Attached scsi disk sda at scsi0, channel0,id0,lun0

I had to type, all of this, in manually because I still need to sort the floppy mount problem.

---

