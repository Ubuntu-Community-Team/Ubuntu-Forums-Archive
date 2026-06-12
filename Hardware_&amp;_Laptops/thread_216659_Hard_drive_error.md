---
title: "Hard drive error"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by Ocxic on 2006-07-15
I accidently shorted out my power, and now every so often i get theses errors:

```
 sd 0:0:0:0: SCSI error: return code = 0x8000002
[4308768.128000] sda: Current: sense key: Medium Error
[4308768.128000]     Additional sense: Unrecovered read error - auto reallocate failed
[4308768.128000] end_request: I/O error, dev sda, sector 9282359
[4308768.128000] Buffer I/O error on device dm-8, logical block 1160239
[4308771.793000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[4308771.793000] ata1: status=0x51 { DriveReady SeekComplete Error }
[4308771.793000] ata1: error=0x40 { UncorrectableError }
[4308775.459000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[4308775.459000] ata1: status=0x51 { DriveReady SeekComplete Error }
[4308775.459000] ata1: error=0x40 { UncorrectableError }
[4308779.108000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[4308779.108000] ata1: status=0x51 { DriveReady SeekComplete Error }
[4308779.108000] ata1: error=0x40 { UncorrectableError }
[4308782.765000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[4308782.765000] ata1: status=0x51 { DriveReady SeekComplete Error }
[4308782.765000] ata1: error=0x40 { UncorrectableError }
[4308786.414000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[4308786.414000] ata1: status=0x51 { DriveReady SeekComplete Error }
[4308786.414000] ata1: error=0x40 { UncorrectableError }
[4308786.414000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[4308786.414000] sda: Current: sense key: Medium Error
[4308786.414000]     Additional sense: Unrecovered read error - auto reallocate failed

```

this has happend befor and a format has fixed the problem i was wondering if there was a way to fix this problem, all of my data is still there and i can mount with no problems. fsck says everything is fine. any ideas???

---

### Post by mooseman089 on 2006-07-15
Does yours even boot up to ubuntu at all? I'm having almost the same problem and a few days before it happened the power did go out so I dont know if there is a connection but for me ubuntu won't boot up at all

---

### Post by Ocxic on 2006-07-16
mine will boot to a point then freeze, I can boot with a live cd and get access to all my data and everything

---

### Post by mooseman089 on 2006-07-16
Yea mine is weird the ubuntu live cd won't boot at all for some reason and a new knoppix ver. 5.0.1 boots but doesnt see the main drive but an older knoppix 3.9 i had laying around for some reason did see the main drive and let me get my files but I think my issue  is with my motherboard so I'm going to try to RMA it to newegg sometime next week because we are going on a little vacation this week

---

### Post by mike_d on 2006-09-06
has anyone found a solution to this error?  i got a new dell n series today and moved my sata card and 4 sata disks over to it and was able to install ubuntu fresh with no issues.  i used an old dapper pre release cd to do the installation.  everything worked fine until i did my apt-get update && apt-get dist-upgrade.  now the computer will not boot as long as the sata drives are in the computer.  i get the same error messages as the original poster.  the disks and controller card worked just fine in my old computer, so i'm guessing it's a software error somewhere. just don't know what's going on.

---

### Post by nparrott on 2008-02-01
I am experiencing this also!?  Has anyone ever figured anything out as to why this may be happening?

Thanks!

---

### Post by Ocxic on 2008-02-01
hi,yes i have actually.. bad news though. My 200 GB SATA drive it seems is failing, over 1.3 million ECC corrected errors, not good. The drives only a year old too, got it last x-mas. I'm using spinrite to run the tests. although all of my sectors appear good, I believe I'm still gonna go check my warranty anyways.
check you manufactures website or try using spinrite (it's very through, excellent program.

---

