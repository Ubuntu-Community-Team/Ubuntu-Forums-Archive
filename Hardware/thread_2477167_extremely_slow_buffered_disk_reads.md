---
title: "extremely slow buffered disk reads"
date: 2022-07-16
forum: Hardware
---

### Post by fw407 on 2022-07-16
Hello,

Somehow my HDD disk I/O is very slow. Below is the output of hdparm. The buffered disk reads is extremely slow. Could someone shine some light on this problem please?

Thanks,
Feng

Ubuntu version
----------------------------------------
lsb_release -a
---------------------------------------
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:    20.04
Codename:    focal


------------------------------------------------------------------------
sudo hdparm -Tt /dev/sda
------------------------------------------------------------------------
/dev/sda:
 Timing cached reads:   23826 MB in  2.00 seconds = 11926.55 MB/sec
 Timing buffered disk reads:   2 MB in  4.79 seconds = 427.66 kB/sec



---------------------------------------------------------------------------
sudo hdparm -i /dev/sda
-------------------------------------------------------------------------
/dev/sda:

 Model=TOSHIBA MG08ADA400NY, FwRev=GD03, SerialNo=Y1N0A1J2FYXG
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=7814037168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=disabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode
--------------------------------------------------------------------

---

### Post by TheFu on 2022-07-16
Doesn't seem slow to me. Here are mine:
```

$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   16618 MB in  2.00 seconds = 8319.05 MB/sec
 Timing buffered disk reads: 256 MB in  3.02 seconds =  84.66 MB/sec


$ sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   16358 MB in  2.00 seconds = 8188.27 MB/sec
 Timing buffered disk reads: 1250 MB in  3.00 seconds = 416.30 MB/sec

```
One is a Hitachi Deskstar P7K500 and the other is a Micron SATA SSD.
Both disks were doing what they normally do when I ran the hdparm tests, not really busy, but there were 10 VMs running on the SSD.

Don't confuse MB with Mb. That's my only suggestion.  There are specs and then there's the real world.  Sadly, most of us live in the real world.

---

### Post by fw407 on 2022-07-16
I think yours look alright. My "buffered disk reads" is 427.66 kB/sec (please see my original post). When I read/write a small text file, it sometimes takes a while.

I am wondering what is going wrong.....

---

### Post by TheFu on 2022-07-17
> **fw407 said:**
> I think yours look alright. My "buffered disk reads" is 427.66 kB/sec (please see my original post). When I read/write a small text file, it sometimes takes a while.

I am wondering what is going wrong.....

Ah ... sorry, since code tags weren't used, I missed the kB vs MB.  I'd look at the SMART data to see what it says.  Often, a bad cable will be shown in the SMART data through CRC errors while nothing else shows any issues.
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   099   099   016    Pre-fail  Always       -       2
199 UDMA_CRC_Error_Count
```
are the parameters to check. Use the raw values, not the others, which are worthless.  A few aren't concerning. But ... 
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       462
```
No read errors, butr CRC errors - probably a cable that needs replacement ... or at least a connector that needs to be re-seated.

---

