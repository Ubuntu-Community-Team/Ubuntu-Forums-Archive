---
title: "No drives on boot"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by gfs on 2005-04-09
I am trying Ubuntu 5.0.4 livecd.
It does not recognize any drives on boot-up.  It only recognized the CD-ROM drive.
What am I doing wrong?

---

### Post by edubarr on 2005-04-09
[QUOTE=gfs]I am trying Ubuntu 5.0.4 livecd.
It does not recognize any drives on boot-up.  It only recognized the CD-ROM drive.
What am I doing wrong?[/QUOTE]
 Are they IDE, SCSI or SATA disks? IDE disks are pretty straight forward, it shouldn't be a problem. SCSI and SATA are a little different though, more info would help in pin-pointing the problem.

---

### Post by gfs on 2005-04-10
They are IDE and SCSI (USB).
There are no entries for hda1, hda2, fd0, sda in fstab.

---

### Post by alastair on 2005-04-10
LiveCD? ATA or SATA? 

Try and check the logs i.e. boot up logs in :

/var/log/syslog

Look for IDE probe/SATA/SCSI messages etc.

Also : lspci -v

Basically, more detail.

---

