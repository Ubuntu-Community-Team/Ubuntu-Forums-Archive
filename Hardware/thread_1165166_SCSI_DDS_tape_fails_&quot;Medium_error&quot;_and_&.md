---
title: "SCSI DDS tape fails &quot;Medium error&quot; and &quot;error on write filemark&quot;"
date: 2009-05-20
forum: Hardware
---

### Post by henrylaw on 2009-05-20
I'm trying to get an HP DDS2 tape to work with my Ubuntu 8.04 desktop system. I've tried various combinations of tar and dd but on every occasion I get things like this (this is a dd example but it's the same all the time)[INDENT][FONT=Courier New]henry@saturn:~$ sudo dd if=lr.txt of=/dev/st0 obs=512 
dd: writing to `/dev/st0': Input/output error 
dd: closing output file `/dev/st0': Input/output error[/FONT]
[/INDENT]... associated with log entries like this:[INDENT][FONT=Courier New][16743.478185] st0: Sense Key : Medium Error [deferred]
[16743.478200] st0: Add. Sense: Sequential positioning error
[16775.895007] st0: Sense Key : Medium Error [deferred]
[16775.895022] st0: Add. Sense: Sequential positioning error
[16775.895033] st0: Error on write filemark.[/FONT]
[/INDENT]I've tried three tape drives, two SCSI adapter cards and three different cables, using both device-internal termination (one of the drives does that) and also a separate terminator on the cable; the faults are all more or less the same, from which I deduce that it's not a hardware problem, but something I'm doing wrong!

The permissions on the tape device look OK (assuming I run under sudo), and the cartridge is not write-protected.[INDENT][FONT=Courier New]crw-rw---- 1 root tape 9, 0 2009-05-20 14:29 /dev/st0[/FONT]
[/INDENT]I've tried everything I can think of: can someone here suggest where I might go to debug this and find the cure?

It's quite important, because when I get it working I then need to recover some quite important data from some old tapes.

---

### Post by twopoint718 on 2009-11-24
Bump

---

### Post by henrylaw on 2009-11-24
Yes, bump indeed; I'm no further on with this.  In fact I'm further back, because I've tried no fewer than three different tapes (two HP, one Seagate/Python), three SCSI cards (Advansys, IWill and Adaptec), two ribbon cables and three tapes, with and without termination both external and internal ... and still get the same kinds of errors, though they're slightly different among the drives.  "Sequential positioning error" is one of the messages too.  

I'm convinced it's nothing to do with the hardware, but that doesn't help me much with finding out what it is to do with.

---

