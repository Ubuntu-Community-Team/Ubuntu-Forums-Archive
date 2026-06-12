---
title: "Feisty DVDRW SATA not burning"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by xerman on 2008-02-01
Hello there,

I am trying to burn a series of Backup DVDs, with photos from digital camera, work at office, and music. Different DVDs for each use. So files are of different kind in every DVD.

The Burner is an LG Supermulti DVDRW-DL SATA (Hardware info reports as SCSI, as both HD drives).
OS is Ubuntu Feisty up to date with Compiz enabled.

Apps used to burn: GnomeBaker, Brasero, CD/DVD Creator.

I even tried to make an iso image with the data and then burn the iso image to disk.

Results, regarding the app used, is UNUSABLE DISK with some recording done, but not the whole info. Depending on de app the surface recorded differs.
Does not depend on the write speed. Set to Auto, or to something lower than 8x (media max) makes the same result.

The error produced by GnomeBaker when trying to burn DVD-R is:
```
/dev/sr0: engaging DVD-R DAO upon user request...
/dev/sr0: reserving 1685241 blocks
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=e360h failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
```

Trying to burn a CD produces the following:
```
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 17870 kB/s 101x CD 12x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 8468 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 9B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.002s timeout 40s
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 317440 bytes
Writing  time:   13.024s
Average write speed 357.0x.
Fixating...
Fixating time:   13.960s
```

So there is no way to burn nor a CD nor a DVD with this Burner. And there is no way to set DMA to 1(result of sudo hdparm -d1 /dev/sr0):
```
/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

After looking at some more posts, i tried to run Gnomebaker as root, but with the same results:
```
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 18070 kB/s 102x CD 13x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 8468 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 9B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.004s timeout 40s
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 317440 bytes
Writing  time:   13.016s
Average write speed 357.1x.
Fixating...
Fixating time:   13.929s
```

Thanks for comments or help.

---

### Post by xerman on 2008-02-05
Hello there:

After diggin for a while on the net, seems that this is a Kernel Issue.

uname -a produces:

```
Linux xlar 2.6.20-16-generic #2 SMP Tue Dec 18 05:45:12 UTC 2007 i686 GNU/Linux
```

and seems that SATA DVDRW just records if kernel is above 2.6.22 or something like that...

I'll check again with new version, 8.04 to see if the issue was just this one or there is more stuff related

Regards
Xermán

---

