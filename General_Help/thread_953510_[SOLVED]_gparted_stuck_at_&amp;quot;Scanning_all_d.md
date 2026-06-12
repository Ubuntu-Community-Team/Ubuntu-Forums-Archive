---
title: "[SOLVED] gparted stuck at &amp;quot;Scanning all devices...&amp;quot;"
date: 2008-10-20
forum: General Help
---

### Post by earthpigg on 2008-10-20
so, i was playing with some partitions... and it had an error for some reason, and when the window that pops up when you are changing partitions around closed gparted just got stuck at 'Scanning all devices...'

i closed it and restarted it, the 'scanning all devices' progress bar thing is still moving back and forth.

i started it from the terminal, only output it is giving me is the standard

```
mason@mason-laptop:~$ sudo gparted
[sudo] password for mason: 
======================
libparted : 1.7.1
======================


```

thing.

so, whats up with that?

---

### Post by earthpigg on 2008-10-20
google tells me that this problem is sometimes caused by people with floppy drives (i do not have one) and/or FAT32 partitions (i also have none of those, since i just unplugged my external hd and restarted it and its still 'scanning all devices...' forever again).

the only thing that has changed on my system is the partition mentioned above.

---

### Post by earthpigg on 2008-10-20
running

> gksudo gparted /dev/sda

made it work perfectly. weird.

---

### Post by marshmallow1304 on 2010-06-06
I know this thread is nearly two years old, but I've had this happen before.  It occurred because a floppy drive was activated in the BIOS but no floppy drive was actually attached.  Gparted was looking for a floppy drive that wasn't actually there.

---

