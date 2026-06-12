---
title: "Partitions not working?"
date: 2008-11-07
forum: Hardware
---

### Post by slaya on 2008-11-07
Having trouble partitioning?
Hi, i'm trying to install ubuntu "server" 8.10 on a spare computer of mine with the following specs:

amd athlon xp 1600+
768mb ddr ramn
120gb ATA 100 hard drive
cd-rw ata drive

The install was going smoothly, and detected my hard drive 100%.

Then the partition menu came up, and i followed the guided partition for "use entire disk", the next screen asked me to chose which hard drive i would like to install ubuntu to. Obviously there was a single listing, but the listing was as follows:

"SCSI1 (0,0,0) (sda) - 120.1 GB ATA SAMSUNG SV1204H"

This was weird to me because my drive is IDE/ata, not SCSI? but i continued anyways only to recieve an error messege saying "Input/output error during read on /dev/sda"

What could be the problem to this?
is ubuntu server only for SCSI hard drives?
there is windows currently installed on the drive, must i format before installing ubuntu?

thanks.

---

### Post by kidders on 2008-11-09
Hi there,

> **slaya said:**
> my drive is IDE/ata, not SCSISince about 2.6.19 (I think), many IDE chipsets default to the kernel's libata driver, rather than the legacy IDE ones.

"Input/output error" suggests a physical fault on your disk. You could try checking it for damage, and partitioning/formatting it yourself, before you install. Assuming your disk does have some bad blocks, that's probably the quickest/easiest way to work around them.

---

