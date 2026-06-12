---
title: "Hard drive access very slow"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by pepez on 2008-02-05
My workstation (Kubuntu 7.1) is really sluggish and after checking with ```
sudo hdparm -tT /dev/sda

``` the numbers are horrible.

/dev/sda:
 Timing cached reads:   1966 MB in  2.00 seconds = 982.80 MB/sec
 Timing buffered disk reads:    2 MB in  3.31 seconds = 619.27 kB/sec

The drive is WDC WD2500JS-75NCB1

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13       29300   235255860   83  Linux
/dev/sda3           29301       30394     8787555   82  Linux swap / Solaris

sda1 is ext2, sda2 is xfs.

Is the drive about to fail or what could be the problem? I know this machine used to overheat...

---

### Post by marpstar on 2008-02-05
I'd run it thru a hard drive test. I prefer Hitachi's Drive Fitness Test.  You can download a bootable ISO of the test at [http://www.hitachigst.com/hdd/support/downloads/ftool_208.iso](http://www.hitachigst.com/hdd/support/downloads/ftool_208.iso)

Boot to that, select your drive, run an advance test and go find something to do for an hour or so.  If it comes up failing at the end of the test, It's time to replace the drive.

Hope this helps.

---

### Post by jakommo on 2008-02-05
Is this a SATA or a IDE Drive?

for IDE you could check if DMA is enabled by running 
```
hdparm -v /dev/sda
```
using dma sould be 1.
if its disabled use
```
hdparm -d1 /dev/sda
```
to enable DMA

---

### Post by ipsi on 2008-02-27
I've got a similar issue, and my scores must be utterly abysmal on the hdparm test:

/dev/sda:
 Timing cached reads:   694 MB in  2.00 seconds = 346.93 MB/sec
 Timing buffered disk reads:   80 MB in  3.14 seconds =  25.48 MB/sec

It is apparently a SCSI disk, though not SATA, as the laptop is about 4 years old (Toshiba A10 Satellite).

Could it be overheating and thus underperforming? My fan is quite noisy and needs replacing, but I actually just can't afford it right now (and I'd have to buy two - damn minimum orders...)

---

### Post by Geezle on 2008-03-04
> **jakommo said:**
> Is this a SATA or a IDE Drive?

for IDE you could check if DMA is enabled by running 
```
hdparm -v /dev/sda
```
using dma sould be 1.
if its disabled use
```
hdparm -d1 /dev/sda
```
to enable DMA

I'm having a similar problem...I can enable dma using 
```

hdparm -d1 /dev/hdb 
```
Is there I way it can be set up so I don't have to do this after each time I boot?

---

