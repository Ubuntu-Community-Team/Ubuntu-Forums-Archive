---
title: "Software RAID needed when Bios RAID configured?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by ZiaTioN on 2009-01-10
Hey all,

Had a quick question about setting up a RAID1 (mirrored array) on a phenom x 4 9950 system using the server version of ubuntu 8.10.  My mobo Bios supports RAID configuration so I have setup a RAID1 array in my bios.  The issue is that I initially attempted to install the standard (non-server) version via the live cd but the disk partitioner still showed two separate physical drives as apposed to a single drive backed up by a mirror.

Since this was the case, I assumed I had to still configure a software RAID by manually partitioning the system and creating the RAID devices.  I attempted to do this but this non-server version does not allow for the configuration of a software RAID so I downloaded the server version.

Now with the server version, I get to the disk partioning portion and only a single RAID array disk is shown (like I thought should have happened the first time).  My question is, since the server version recognizes the bios RAID, do I still need to configure a software RAID in the OS?  A second question is, why did the non-server version not recognize the bios RAID but the server version does?  I have read that in order for mobo bios RAIDs to be recognized that the OS has to have drivers that will support the bios RAID and therefore recognize it.  Is this what is happening between the server and non-server versions of 8.10?

---

