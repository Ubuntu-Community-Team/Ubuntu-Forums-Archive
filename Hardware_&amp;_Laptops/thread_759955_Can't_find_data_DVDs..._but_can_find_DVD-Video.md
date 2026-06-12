---
title: "Can't find data DVDs... but can find DVD-Video"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by pianoman on 2008-04-19
Hi, I've got a few problems with DVD detection:


- I've got a CD/DVD SuperMulti drive on a laptop running Gutsy.

- All CD's, Commercial DVD-Video works fine, no problems

- When I put data DVDs in the drive, the drive light flickers and i can hear the drive seeking but [mount] says no media in drive.

- I heard that there were problems with the way disc formats were read in fstab but setting the device format section to "udf, iso9660", "iso9660, udf" or "auto" makes no difference.

- Curious thing, looking at the output of [lshal] shows that HAL is not detecting some of the capabilities of my drive (storage.cdrom.dvdplusrwdl and storage.cdrom.dvdram both false, should be true)

- The plot thickens. Attempting to boot from DVD takes far longer and I can hear the drive trying to seek but it still can't find anything. I know its at least trying to boot as I have checked BIOS boot order.

Any ideas on how to get the drive working?

Thanks in advance!

---

### Post by pianoman on 2008-05-09
UPDATE: Now my drive doesn't detect DVD-Video 100%, I sometimes have to eject and reinsert the disc, though this is rare. Is my drive screwed?

---

### Post by timcredible on 2008-05-09
possibly.  however, with the data dvds, does your drive work with dvd-r, dvd+r, or both?  make sure it can actually read the format of the disk you put in the drive.

---

### Post by pianoman on 2008-05-20
hey - sorry for the late reply - exam season at university

so far i've got that dvd-video mounts, dmesg detects a udf filesystem and automounts as expected. dvd+r and dvd-rom don't load - even though i can hear the drive seeking, dmesg shows nothing.

Even more interesting - written cd-r's are showing up as blank. my friend runs them on a windows machine, everythings there... on my hardy, nothing

one last thing, looking through dmesg for boot processes, my box is detecting my drive as a cd-rom and says my 'sr' driver should be updated by a bus_type method - what is this?

Excerpts from dmesg:
```

[   16.060820] ata2.00: ATAPI: _NEC DVD_RW ND-6750A, 2.42, max UDMA/33
[   16.232597] ata2.00: configured for UDMA/33

[   16.239910] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-6750A  2.42 PQ: 0 ANSI: 5

[   16.251145]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   16.309498]  sda1 sda2 < sda5 >
[   16.334433] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.341289] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.341319] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   16.379711] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   16.379719] Uniform CD-ROM driver Revision: 3.20
[   16.379788] sr 1:0:0:0: Attached scsi CD-ROM sr0



```

My device is sr0 so I'm guessing that sr-related stuff is the disc drive

EDIT: oh and i'm now on hardy if it makes any difference

---

