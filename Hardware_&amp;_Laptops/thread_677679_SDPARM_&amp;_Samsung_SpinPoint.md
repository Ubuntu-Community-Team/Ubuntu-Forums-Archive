---
title: "SDPARM &amp; Samsung SpinPoint"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by Mustamakkara on 2008-01-25
Hi !

I have Samsung SpinPoint T166 HD501LJ (500 Gt, serial-ATA II, 16 Mt) - hard drive. Althought it's silent I want to make it even more silent with SDPARM.

I understand that SDPARM is for SATA-drives. Could somebody please help me how to get my hard drive to "Quiet"-mode ? Other tuning isn't needed.

Thanks for your support allready beforehand !

---

### Post by Yellow Pasque on 2008-01-25
I have a similar drive and I don't see an option for it. How do you have your hard disk mounted? You didn't screw it into the chassis, did you? If so, get some foam and rest the disk on that (or you can suspend it with elastic). Just make sure it isn't touching the case/chassis. That will make a huge difference in the noise. These drives are very quiet, but they vibrate like an adult toy.

```
dan@harvest:/usr/bin$ sdparm /dev/sda -a -l
    /dev/sda: ATA       SAMSUNG HD321KJ   CP10
    Direct access device specific parameters: WP=0  DPOFUA=0
Read write error recovery [rw] mode page:
  AWRE        1  Automatic write reallocation enabled
  ARRE        0  Automatic read reallocation enabled
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
  WCE         1  Write cache enable
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

### Post by Mustamakkara on 2008-01-25
Thanks for your reply.

Yes ... unfortunately I screwed it into the chassis ;-(

Would this help enough ? Or any other ideas like this ?

[http://www.nexustechnologyusa.com/c/ntusa/disktwin_aluminum.html](http://www.nexustechnologyusa.com/c/ntusa/disktwin_aluminum.html)

I allready have Nexus 500 Breeze as case ...

---

### Post by Yellow Pasque on 2008-01-25
There's a wealth of info on silencing components on SPCR. I draw your attention to this thread in their forum: [http://www.silentpcreview.com/forums/viewtopic.php?t=8240](http://www.silentpcreview.com/forums/viewtopic.php?t=8240)

---

### Post by Bartender on 2008-01-25
Here's my elastic mount, just to give you an idea.

This is inside of a wood cabinet, so I was free to set it up however I wanted.  Working within the confines of a case can be harder.  
My first attempt at elastic mounting was inside a Sonata.  The removable side panel would start buzzing like a fly caught in a window whenever the HDD was busy.  Highly annoying for a "silent" case.
I suspended the HDD with some shock cord.  Amazing difference.  You couldn't hear the HDD activity unless you stuck your ear up against the side of the PC.

I'd sure try soft-mounting the HDD before screwing around with sdparm.

---

