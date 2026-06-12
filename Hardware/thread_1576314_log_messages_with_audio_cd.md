---
title: "log messages with audio cd"
date: 2010-09-17
forum: Hardware
---

### Post by dafreez on 2010-09-17
Hi,

I have an odd problem. Whenever I place an audio CD in my drive (optiarc AD5260S DVD RW) an insane amount of messages get written to syslog, kern.log messages in /var/log. They all look like this:

```
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.813793] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.813795] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.813798] sr 2:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.813801] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 06 00 00 02 00
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.813806] end_request: I/O error, dev sr0, sector 24
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.815762] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.815766] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.815769] sr 2:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.815774] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 06 00 00 02 00
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.815782] end_request: I/O error, dev sr0, sector 24
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.818131] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.818133] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.818136] sr 2:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.818139] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 0e 00 00 02 00
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.818144] end_request: I/O error, dev sr0, sector 56
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.820162] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.820166] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.820170] sr 2:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.820174] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 0e 00 00 02 00
Sep 17 09:22:38 dafreez-desktop kernel: [ 4572.820181] end_request: I/O error, dev sr0, sector 56
```

Only the sector numbers and the numbers following read(10) change. These lines written at a rate of a few MB per second. This means that if I accidentally leave an audio CD in overnight it completely floods my system file partition.
The thing is: the drive works fine. I can play/rip/burn CDs and DVDs. Also data discs and DVDs do not give any error messages

One final note:The  problem is worse when the disc is idle. When I actually play/rip an audio CD fewer or no errors get written to the logs.

Anyone have any idea what might be causing this and how I could solve it?

---

### Post by dafreez on 2010-09-27
Anyone have any idea what is causing this?

---

### Post by dafreez on 2010-09-27
This appears solved with kernel upgrade 2.6.32.25

---

### Post by karsten_df on 2010-10-05
hi dafreez,

I seem to have a similar problem (I've opened a new thread _[http://ubuntuforums.org/showthread.php?t=1588667](http://ubuntuforums.org/showthread.php?t=1588667)_[]("http://ubuntuforums.org/showthread.php?p=9927162#post9927162"), since yours is marked as solved).

(There is a slight difference in log messages though - an additional line "Info fld=0x0, ILI")

I'm running kernel 2.6.32.25 on a headless 10.04 server, so I'd be curious whether you'd still feel that the problem did disappear with above kernel upgrade?

regards -

Karsten

---

### Post by dafreez on 2010-10-06
> **karsten_df said:**
> hi dafreez,

I seem to have a similar problem (I've opened a new thread _[http://ubuntuforums.org/showthread.php?t=1588667](http://ubuntuforums.org/showthread.php?t=1588667)_, since yours is marked as solved).

(There is a slight difference in log messages though - an additional line "Info fld=0x0, ILI")

I'm running kernel 2.6.32.25 on a headless 10.04 server, so I'd be curious whether you'd still feel that the problem did disappear with above kernel upgrade?

regards -

Karsten

Yes it does seem solved. Although when I put an audio CD in a few hundred lines of these messages are logged (about 0.1MB worth) it then stops. Also I shoulkd note that even when the problem occurred, it did not in any way effect the functioning of the drive. I could play and rip cd's perfectly and in fact using the drive caused the log messages to stop.

Good luck! I didn't find any solutions untill the kernel upgrade fixed it...

---

