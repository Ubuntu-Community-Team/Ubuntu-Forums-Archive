---
title: "ubuntu not reading dvds"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by aa.ivanov on 2007-02-15
I'm trying to write archives to dvds on my laptop under Edgy. It's not working for some wild reason.

Creating ISOs is not a problem - I can mount the iso files I've made and verify the files' checksums. Writing to dvd disk seems to work - no error is reported, buffer is not dropping under 96%. Reading the disk on the same computer under ubuntu fails even though I can read the disk on other machines (both windows and linux). I can even read the disk under the almost forgotten Windows XP that came with my laptop. Reading under ubuntu fails and the following error is sent to /var/log/messages a number of times:
```
Feb 14 18:22:43 frodo kernel: [17530573.956000] attempt to access beyond end of device
Feb 14 18:22:44 frodo kernel: [17530573.956000] sr0: rw=0, want=2097152, limit=2097151
Feb 14 18:22:44 frodo kernel: [17530573.956000] attempt to access beyond end of device
Feb 14 18:22:44 frodo kernel: [17530573.956000] sr0: rw=0, want=2097156, limit=2097151
Feb 14 18:22:44 frodo kernel: [17530573.956000] attempt to access beyond end of device
Feb 14 18:22:44 frodo kernel: [17530573.956000] sr0: rw=0, want=2097160, limit=2097151
Feb 14 18:22:44 frodo kernel: [17530573.956000] attempt to access beyond end of device
Feb 14 18:22:44 frodo kernel: [17530573.956000] sr0: rw=0, want=2097164, limit=2097151
```
The 'want' and 'limit' vary of course.

I've been trying to write the disks with brasero, nautilus, k3b and growisofs... the effect is just the same (as could be expected). I've tried writing on DVD-Rs on DVD+Rs... no difference.

The DVD burner is a SATA device, but I can't figure out the brand:
```
$ hdparm -i /dev/dvd

/dev/dvd:
 HDIO_GET_IDENTITY failed: Function not implemented
$ hdparm -I /dev/dvd

/dev/dvd:
 HDIO_DRIVE_CMD(identify) failed: Function not implemented
$ sudo cdrecord -scanbus 
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-11-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'ATA     ' 'Hitachi HTS54168' 'SB2O' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
scsibus1:
        1,0,0   100) 'HL-DT-ST' 'DVDRAM GMA-4082N' 'PT06' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

```

Can anyone give me a clue how to deal or at least what's causing that strange behavior?

---

### Post by aa.ivanov on 2007-02-17
Hmm it seems like i have figured it out.

For unknown reason 386 kernel was marked as default for my ubuntu. I've switched to the generic kernel and this seems to have solved the issue. 
Still it looks rather strange to me that 386 kernel is unable reading more than 1.1GB from dvd.

---

### Post by meng on 2007-02-17
That is weird. Glad it works for you now.

---

### Post by aa.ivanov on 2007-03-10
Seems I was wrong about the kernel :(
[http://ubuntuforums.org/showthread.php?p=2275217#post2275217](http://ubuntuforums.org/showthread.php?p=2275217#post2275217)

---

