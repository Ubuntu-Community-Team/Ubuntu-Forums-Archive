---
title: "Software RAID 5 on older system (2 questions)"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by jgoney on 2009-07-18
Hi!
 
I currently have a home LAMP server running Jaunty server edition. It's for essentially personal use (FTP, Ampache, backups, etc.), so it doesn't see a lot of traffic. It's an older machine: Pentium 4 1.5 GHz with 1.5 GB RAM.

Currently I have a software RAID 1 setup with 2 500 GB drives, which works great except I'm out of space. I'm looking into RAID 5 since you lose less disk capacity that way. So here are my two questions...

1. Will an older system like this support the extra overhead of software RAID 5?

2. Since mdadm looks for partitions rather than disks, I'm thinking of adding a 1 TB disk partitioned into 2 partitions; one 500 GB that goes with the other two 500 GB disks in the RAID, and the second as a regular non-RAID partition for non-critical files. Does anyone see any potential problems with this approach? I realize that if the larger drive fails I'll lose the non-RAID data.

Thanks in advance for your replies. Let me know if you need more information.

 - Justin

P.S. - I'm not planning on booting from the RAID.

---

