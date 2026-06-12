---
title: "Manually Mounting a USB Drive"
date: 2010-04-03
forum: Hardware
---

### Post by Psumi on 2010-04-03
[http://www.novell.com/coolsolutions/feature/11637.html](http://www.novell.com/coolsolutions/feature/11637.html)

I was going through this tutorial linked above, but then when I got to the **dmesg | grep -i** portion, I thought for a moment and said to myself, "Wait, I don't have that kind of output.

Which is true,

dmesg | grep -i "SCSI device" outputs
```
nothing
```

where

dmesg | grep -i "SCSI" outputs
```
[    0.436103] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.589321] SCSI subsystem initialized
[    4.096573] scsi0 : SCSI emulation for USB Mass Storage devices
[    9.102665] scsi 0:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[    9.369117] sd 0:0:0:0: [sda] Attached SCSI removable disk
```

So how do I manually mount a USB drive after I've first installed the base CLI system (using mini.iso) to a linux distro such as ubuntu or Debian?

---

### Post by Psumi on 2010-04-03
Found out what to use,

it's /dev/sda1 and not /dev/sda.

---

