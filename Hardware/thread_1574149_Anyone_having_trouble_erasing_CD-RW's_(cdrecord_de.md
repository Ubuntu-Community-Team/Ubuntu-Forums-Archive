---
title: "Anyone having trouble erasing CD-RW's? (cdrecord /dev/cdrom1 blank=fast)"
date: 2010-09-13
forum: Hardware
---

### Post by tgp1994 on 2010-09-13
Hi everyone.

Seems I'm having trouble with the CD writing system of ubuntu. First, using gnomebake, it would never even touch my CD-RW when I tried to burn an ISO, and leave all of the original data intact.

Now, when I'm trying to erase it from a terminal, it just sits there, erasing my CD (supposedly) while being an unkillable process.

I haven't tried the erasing process again, but I'm just wondering if anyone has experienced this/has any information regarding it. Here's the entire section of my terminal:

[quote=Terminal]
~ $ cdrecord /dev/cdrom1 blank=fast
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX230ED '
Revision       : '4YS1'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
wodim: WARNING: Total disk size unknown. Data may not fit on disk.
Speed set to 706 KB/s
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.


(Hour and a half has elapsed at this point...)

^C^C^C^C
[/quote]


Please also see [this bug](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/637684) for more information.

---

### Post by tgp1994 on 2010-09-13
Bump :S

---

### Post by tgp1994 on 2010-09-14
Bump :neutral:

---

### Post by tgp1994 on 2010-09-14
Nevermind, I solved this through the help of the irc room. Turns out I had to run the program under sudo, which I believe is still a bug, since my drive should be under control from all users, and, really... that program shouldn't completely freeze up just because I didn't run it with elevated permissions.

---

