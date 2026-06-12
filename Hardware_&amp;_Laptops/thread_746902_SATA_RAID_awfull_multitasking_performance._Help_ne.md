---
title: "SATA RAID awfull multitasking performance. Help needed"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by digoart on 2008-04-06
Hi , 

I've got a problem on multitasking on my quite powerfull server.

n short, doing anything like:

$ tar zxfp largesourcecodearchive.tar.gz

(or anything fairly disk i/o intensive, but especially that type of thing)

...brings my system to it's knees. although the extraction moves along
fairly quickly, all other tasks on my system happen at an unnacceptably slow
rate.

as this is going to be a multi-user system, it is not acceptable to have one
user's source code extraction cause all other user's processes be slown to a
complete crawl. in fact, in my case, this amounts to a local
denial-of-service issue. extracting three or more tar archives at once
causes the entire system to nearly stop responding until they're finished.

Any ideas how I can tune it with sdparm taking in mind my mirrored RAID? 

My disk parameters:

```

# hdparm -i /dev/sda
/dev/sda:

 Model=ST3250820AS                             , FwRev=3.AAE   , SerialNo=            6QE1QBQ5
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no WriteCache=disabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

------------------------------------------------
# hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   3136 MB in  2.00 seconds = 1569.41 MB/sec
 Timing buffered disk reads:  156 MB in  3.02 seconds =  51.71 MB/sec

--------------------------------------------------
# sdparm  /dev/sda -a -l
    /dev/sda: ATA       ST3250820AS       3.AA
    Direct access device specific parameters: WP=0  DPOFUA=0
Read write error recovery [rw] mode page:
  AWRE        1  Automatic write reallocation enabled
  ARRE        1  Automatic read reallocation enabled
  TB          0  Transfer block
  RC          0  Read continuous
  EER         0  Enable early recovery
  PER         0  Post error
  DTE         0  Data terminate on error
  DCR         0  Disable correction
  RRC         0  Read retry count
  COR_S       0  Correction span (obsolete)
  HOC         0  Head offset count (obsolete)
  DSOC        0  Data strobe offset count (obsolete)
  WRC         0  Write retry count
  RTL         0  Recovery time limit (ms)
Caching (SBC) [ca] mode page:
  IC          0  Initiator control
  ABPF        0  Abort pre-fetch
  CAP         0  Caching analysis permitted
  DISC        0  Discontinuity
  SIZE        0  Size enable
  WCE         0  Write cache enable
  MF          0  Multiplication factor
  RCD         0  Read cache disable
  DRRP        0  Demand read retention priority
  WRP         0  Write retention priority
  DPTL        0  Disable pre-fetch transfer length
  MIPF        0  Minimum pre-fetch
  MAPF        0  Maximum pre-fetch
  MAPFC       0  Maximum pre-fetch ceiling
  FSW         0  Force sequential write
  LBCSS       0  Logical block cache segment size
  DRA         0  Disable read ahead
  NV_DIS      0  Non-volatile cache disable
  NCS         0  Number of cache segments
  CSS         0  Cache segment size
Control [co] mode page:
  TST         0  Task set type
  TMF_ONLY    0  Task management functions only
  D_SENSE     0  Descriptor format sense data
  GLTSD       1  Global logging target save disable
  RLEC        0  Report log exception condition
  QAM         0  Queue algorithm modifier
  QERR        0  Queue error management
  RAC         0  Report a check
  UA_INTLCK   0  Unit attention interlocks control
  SWP         0  Software write protect
  ATO         0  Application tag owner
  TAS         0  Task aborted status
  AUTOLOAD    0  Autoload mode
  BTP        -1  Busy timeout period (100us)
  ESTCT      30  Extended self test completion time (sec)



```

---

### Post by bsmith1051 on 2008-04-08
I believe this is a known issue -- 'server bias' -- in the current kernel configuration.  Basically, background tasks get excessive preference.  So, I don't think the problem is in your RAID configuration.  The next release of Ubuntu (which uses a newer kernel) should use a new 'scheduler' which is supposed to be smarter about this stuff.

---

