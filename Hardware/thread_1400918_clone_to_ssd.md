---
title: "clone to ssd"
date: 2010-02-07
forum: Hardware
---

### Post by mfox on 2010-02-07
I have a multi-boot system in my netbook that includes Win xp home, Ubuntu, and another Linux distro.  The internal HD is 160gb, but most of it isn't used.  I just bought a 60gb SSD, and would like to use it as the primary disk in my netbook.  I would like to clone the Win xp and Ubuntu volumes to the SSD, which would leave me plenty of space, even if I added another distro later.  With gparted, I can see that there is an initial logical volume of about 4gb (dev/sda1) with 775mb used, and by mounting and checking it I can see that it has a boot folder in it.  It is formatted as ext3 (no flags).  I don't understand the MBR concept very well, so I'm wondering if this is where the MBR is stored.  The next volume is my Windows volume and is formatted NTFS with a boot flag.  Subsequent volumes are clearly Linux volumes, including swapfile volumes.  I have already formatted the SSD as NTFS, but as of yet haven't added any partitions.

My question:
(1) How do I clone the volumes I want onto the SSD?  (Presumably with dd or a similar utility).
(2) Does the destination volume have to be initially set to be the same as the source volume?
(3) Do I need that first partition or would a new one automatically be created if I reinstall Ubuntu from scratch or use a utility to fix the MBR?

Thanks!

---

### Post by vanjeje on 2010-02-22
Hello,

I read some SSD disks have more than 512 bytes sector size.
I am currently trying to clone a LiveUSB partition from a micro SDHC to another micro SDHC, but it does not boot... and it is totally inefficient on my disk with 4kB sector size!

See [here]("http://ubuntuforums.org/showthread.php?t=1410900&highlight=duplicating") (and maybe [here]("http://ubuntuforums.org/showthread.php?t=599599&highlight=backup+system+restore+boot")).

---

