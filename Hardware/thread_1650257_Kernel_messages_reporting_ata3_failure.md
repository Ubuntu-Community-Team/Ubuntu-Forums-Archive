---
title: "Kernel messages reporting ata3 failure"
date: 2010-12-21
forum: Hardware
---

### Post by duncan3dc on 2010-12-21
Hi,

This morning one of my computers that I use as a file server, among other things, started becoming unresponsive. After a couple of reboots and stopping some daemons the problem was still occurring.

My /var/log/messages file is flooded with the errors shown below, I assumed that ata3 referred to /dev/sdc however when I unmounted this drive and commented the fstab entry the errors still continued.

Can anyone shed any light on this for me?

Dec 21 15:50:07 metropolis kernel: [ 1655.040037] ata3: lost interrupt (Status 0x50)
Dec 21 15:50:07 metropolis kernel: [ 1655.040992] ata3: soft resetting link
Dec 21 15:50:07 metropolis kernel: [ 1655.280263] ata3.00: configured for UDMA/133
Dec 21 15:50:07 metropolis kernel: [ 1655.347599] ata3.01: configured for UDMA/33
Dec 21 15:50:07 metropolis kernel: [ 1655.347609] ata3.01: device reported invalid CHS sector 0
Dec 21 15:50:07 metropolis kernel: [ 1655.347621] ata3: EH complete

Thanks,

---

