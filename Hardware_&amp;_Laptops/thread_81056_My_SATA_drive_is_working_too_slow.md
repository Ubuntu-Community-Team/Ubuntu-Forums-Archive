---
title: "My SATA drive is working too slow"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by yorick on 2005-10-23
Hello

I have a problem with my Seagate 200 GB SATA drive. It is attached to my Abit NF7-S Motherboard on an Silicon Image 3112a controller. Breezy is installed on the second partition (sda2) and WinXp in the first partition.
I also have a Pionner DVDRW as hda, a 40 GB Maxtor as hdb and a Sony CDRW as hdc. My processor is an AMD Athlon XP 1700+.

The problem is that the SATA drive is working too slow. Between it's partitions I get 8-10MB/s and between the SATA drive and the 40GB one about 4-5MB/s. This is when in WinXP I get about 15MB/s and 45-50MB/s, respectively.

Could anyone tell me what could I do to speed up the SATA drive?

Here are the outputs of some relevant commands:

```
sudo hdparm -tT /dev/sda
Password:

/dev/sda:
 Timing cached reads:   1424 MB in  2.00 seconds = 711.75 MB/sec
 Timing buffered disk reads:   58 MB in  3.03 seconds =  19.15 MB/sec
```

(I read somewhere that these values shold be somewhere above 1000MB/sec and 50 MB/s)

```
sudo hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   1188 MB in  2.08 seconds = 570.14 MB/sec
 Timing buffered disk reads:  146 MB in  3.01 seconds =  48.45 MB/sec

```

```
lsmod | grep sata
sata_sil                9604  15
sata_nv                 9412  0
libata                 54020  2 sata_sil,sata_nv

```

```
sudo hdparm -i /dev/hdb

/dev/hdb:

 Model=Maxtor 6E040L0, FwRev=NAR61590, SerialNo=E15SYKXE
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=80293248
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode
```

```
sudo hdparm -i /dev/sda

/dev/sda:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

```

Any help would be greatly appreciated. Thanks in advance.

---

### Post by 23meg on 2005-10-23
not sure if this will help but to the best of my knowledge hdparm doesn't work with SATA drives except for displaying basic info. instead, there's the "sdparm" utility which i reckon is not as mature as hdparm yet. it must be in the repositories.

---

### Post by yorick on 2005-10-24
Thanks for your reply. I've tried sdparm but I don't know how to interpret the results. Here is the output I get:

```
sudo sdparm -al /dev/sda
    /dev/sda: ATA       ST3200822AS       3.01
Read write error recovery [PS=0] mode page:
  AWRE        1  [ sav:  1]  Automatic write reallocation enabled
  ARRE        1  [ sav:  1]  Automatic read reallocation enabled
  TB          0  [ sav:  0]  Transfer block
  RC          0  [ sav:  0]  Read continuous
  EER         0  [ sav:  0]  Enable early recover
  PER         0  [ sav:  0]  Post error
  DTE         0  [ sav:  0]  Data terminate on error
  DCR         0  [ sav:  0]  Disable correction
  RRC         0  [ sav:  0]  Read retry count
  WRC         0  [ sav:  0]  Write retry count
  RTL         0  [ sav:  0]  Recovery time limit (ms)
Caching (SBC) [PS=0] mode page:
  IC          0  [ sav:  0]  Initiator control
  ABPF        0  [ sav:  0]  Abort pre-fetch
  CAP         0  [ sav:  0]  Caching analysis permitted
  DISC        0  [ sav:  0]  Discontinuity
  SIZE        0  [ sav:  0]  Size (1->CSS valid, 0->NCS valid)
  WCE         1  [ sav:  1]  Write cache enable
  MF          0  [ sav:  0]  Multiplication factor
  RCD         0  [ sav:  0]  Read cache disable
  DRRP        0  [ sav:  0]  Demand read retension priority
  WRP         0  [ sav:  0]  Write retension priority
  DPTL        0  [ sav:  0]  Disable pre-fetch transfer length
  MIPF        0  [ sav:  0]  Minimum pre-fetch
  MAPF        0  [ sav:  0]  Maximum pre-fetch
  MAPFC       0  [ sav:  0]  Maximum pre-fetch ceiling
  FSW         0  [ sav:  0]  Force sequential write
  LBCSS       0  [ sav:  0]  Logical block cache segment size
  DRA         0  [ sav:  0]  Disable read ahead
  NV_DIS      0  [ sav:  0]  Non-volatile cache disable
  NCS         0  [ sav:  0]  Number of cache segments
  CSS         0  [ sav:  0]  Cache segment size
Control [PS=0] mode page:
  TST         0  [ sav:  0]  Task set type
  TMF_ONLY    0  [ sav:  0]  Task management functions only
  D_SENSE     1  [ sav:  1]  Descriptor format sense data
  GLTSD       1  [ sav:  1]  Global logging target save disable
  RLEC        0  [ sav:  0]  Report log exception condition
  QAM         0  [ sav:  0]  Queue algorithm modifier
  QERR        0  [ sav:  0]  Queue error management
  RAC         0  [ sav:  0]  Report a check
  UA_INTLCK   0  [ sav:  0]  Unit attention interlocks controls
  SWP         0  [ sav:  0]  Software write protect
  ATO         0  [ sav:  0]  Application tag owner
  TAS         0  [ sav:  0]  Task aborted status
  AUTOLOAD    0  [ sav:  0]  Autoload mode
  BTP        -1  [ sav: -1]  Busy timeout period (100us)
  ESTCT      30  [ sav: 30]  Extended self test completion time (sec)
```

Could anyone please tell me what is relevant an how and what can I change to make it go faster?

---

### Post by jeremy on 2005-10-24
I can't help you with your problem, but, for your reference, here is my - sudo hdparm -tT /dev/sda - output:
/dev/sda:
 Timing cached reads:   2332 MB in  2.00 seconds = 1165.01 MB/sec
 Timing buffered disk reads:  164 MB in  3.02 seconds =  54.31 MB/sec

I have a seagate SATA 160GB

---

### Post by yorick on 2005-10-24
Hi Jeremy.

Is your conntroller on the motherboard a Silicon Image 3112a too? Because I've done some more searches and I found this [link]("http://www.thisishull.net/archive/index.php/t-23170.html") that suggests there is a problem with this controller used in combination with a Seagate SATA drive. I didn't find out yet if the problem has been fixed until now.

---

