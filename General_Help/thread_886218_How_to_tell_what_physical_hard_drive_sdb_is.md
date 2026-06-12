---
title: "How to tell what physical hard drive sdb is?"
date: 2008-08-10
forum: General Help
---

### Post by zac_haryy on 2008-08-10
I have a RAID 5 setup in my Ubuntu computer and I am trying to figure out what drive is what when I do a "fdisk -l". This is what is shown for that command:
```
Disk /dev/sda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f041

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1186     9526513+  83  Linux
/dev/sda2            1187        1245      473917+   5  Extended
/dev/sda5            1187        1245      473886   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b38a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2edd36e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c4be00f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069a45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4927a977

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf87b4c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 7001.4 GB, 7001415221248 bytes
2 heads, 4 sectors/track, 1709329888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000
```

So basically how do I tell which hard drive is the one that is set to, say "Disk /dev/sdi". Is there any way to make it so that I can switch them around and have "sdb" set as the hard drive that is on top in my computer and then just go down the line. I just want to know this because I am getting errors and have no idea what hard drives are the ones causing the errors. Please let me know, Thanks!

-haryy

---

### Post by Mister.Vash on 2008-08-11
This isn't a blink, but it's what came to mind.

Try doing the following for all the drives in your system

udevinfo --query=all --path /sys/block/sda
udevinfo --query=all --path /sys/block/sdb
etc for each drive

The output from that should list the Vendor/model/serial for each drive that it was run against
Print out the list, open the case, and match up the serial number from the printout to the drive

---

### Post by zac_haryy on 2008-08-11
I will give that a try when I get home from work later today and post what I find. Do the hard drives switch places when the computer is restarted ever? Example: When the computer starts up once sda might be my hefty 10.2gb hard drive and then if the computer gets restarted it might switch to sdi.

-haryy

---

### Post by x1a4 on 2008-08-11
Hi,
I'm not 100% on this but typically
/dev/sda is drive 0 (the first drive)
/dev/sdb is drive 1 (the second drive)
etc

Use Mister.Vash's method to get details about the drive, paying attention to the line beginning with 
[color=blue]S: disk/by-path/pci-[/color]
The end of the line will tell you which disk it is.  On my system when running 
```
udevinfo --query=all --path /sys/block/sdb
```
this line is:
```
S: disk/by-path/pci-0000:00:02.5-scsi-0:0:**1**:0
```. The **1** tells me sdb is disk 1 (second disk).

---

### Post by jpeddicord on 2008-08-11
Moved to General Help (not DE related).

---

### Post by fjgaude on 2008-08-12
One way to get the serial number (SN) of a drive is the command:

```
sudo hdparm -i -v /dev/sd[nn]
```

Then you can physically see which drive it is by noting the SN. You may have to install **hdparm**, it in not by default as I recall.

---

