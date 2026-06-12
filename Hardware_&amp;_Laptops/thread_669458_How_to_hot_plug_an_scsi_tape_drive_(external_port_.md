---
title: "How to hot plug an scsi tape drive? (external port on scsi card)"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by ubtutu on 2008-01-16
If I boot up with the SCSI tape drive plugged in and powered on, my SCSI Tape drive IS detected and /dev/st0 and /dev/nst0 appear in ubuntu 7.10 and work fine for reads and writes using tar. Also the following apears in dmesg: 
```
[   22.368000] scsi 6:0:1:0: Sequential-Access HP       Ultrium 1-SCSI   E34A PQ: 0 ANSI: 3 
```

However if the scsi drive was not present during boot up, I cannot seem to figure out how to hotplug it. I load the SCSITape module using 'modprobe -i st' but do not know where to go from there. Of the following three commands I found on the web:

```
echo "engage scsi" > /proc/driver/cciss/ccissN
echo "rescan" > /proc/scsi/cciss0/1
echo scsi add-single-device 3 2 1 0 > /proc/scsi/scsi
```

The first one doesn't seem to work because the cciss directory does not exist in proc.
The second one, the cciss0 directory does not exist in proc.
The third one gives me permission denied, even if I sudo it.

When booting without the tape drive plugged in at boot time, only SATA drives and the dvdrom drive listed in /proc/scsi/scsi, but not the scsi tape drive, even after plugging it in. I want to tell linux to scan for it, or hot plug it.

Any idea on how to hot plug a SCSI tape drive?

---

### Post by ubtutu on 2008-03-08
bump :)

---

### Post by evanjfraser on 2008-05-08
I just hotplugged a tape drive under ubuntu 8.04 using the same script (rescan-scsi-bus.sh) we use under fedora without any problems.

rescan-scsi-bus.sh which can be found on the authors website here: [http://www.garloff.de/kurt/linux/scsidev/](http://www.garloff.de/kurt/linux/scsidev/)

---

### Post by jtappin on 2008-05-09
I think that scsiadd which is in the universe repositories is intended to do the same thing.

---

### Post by ubtutu on 2008-05-28
Thanks guys!! Ill try these!

---

