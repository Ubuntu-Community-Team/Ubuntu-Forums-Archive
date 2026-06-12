---
title: "Very poor IO performance with HW Raid 1 - Wrong Driver?"
date: 2008-07-22
forum: General Help
---

### Post by bignose on 2008-07-22
G'day.

I'm running a HP DL-145 Server with 2 250g SATA disks in hardware Raid1

admin@base:~$ uname -a
Linux base 2.6.22-14-server #1 SMP Sun Oct 14 22:09:15 GMT 2007 x86_64 GNU/Linux
admin@base:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

It's a dual core opteron with 6 gigs of ram.

dmesg is at [http://www.bignose.ca/scratch/dmesg.txt](http://www.bignose.ca/scratch/dmesg.txt)

The workload is 6 virtual machines running in Vmware-Server 1.04. The demand on the virtual machines is pretty much zero. They just sit there.

Okay, with that out of the way here's the problem. I'm using a Sun Ultra 20 M2 opteron as a comparison machine, it's running LTS and has no raid, but it's "close".

It seems doing some basic read/write tests that the Ultra is up to at least 10 to 50 times faster at everything.. even just something like "man sdparm" can take up to 30 seconds on the DL 145

The device comes up at sda but these lines of dmesg concern me.

[   91.736361] scsi0 : pata_serverworks
[   91.736472] scsi1 : pata_serverworks
[   91.736722] ata1: PATA max UDMA/66 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x0000000000011c00 irq 14
[   91.736823] ata2: PATA max UDMA/66 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x0000000000011c08 irq 15


I can't figure out for the life of me why it would be using a pata driver for anything at all... ? Ideas?

That's what I have for info so far, let me know and I"ll go deeper into the rabbit hole.

---

