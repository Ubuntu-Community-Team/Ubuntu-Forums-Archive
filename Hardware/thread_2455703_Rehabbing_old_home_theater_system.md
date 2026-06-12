---
title: "Rehabbing old home theater system"
date: 2020-12-26
forum: Hardware
---

### Post by JP_Rockagetty_III on 2020-12-26
Hello,

Recently I've been thinking about re-doing my Home Theater system.  I think I used Kodibuntu 16.04 last time.  The hardware:

AsRock AM1H-ITX mini-ITX (I also have an unused NIB MSI version of this lying about).  8 GB RAM, AMD 5350 chip (25W, system-on-a-chip, with a passive heat sink).  I'll use a 120mm fan in the back.

The AsRock board can run 2 SATA drives by using a laptop power adapter, and up to 4 on the mobo with a desktop PSU (I have a couple of laptop adapters and the Seasonic Platinum Fanless 460 with low hours).  The MSI version needs a desktop PSU at all times and only has 2 SATA plugs on the mobo.

Two questions:

(1) Does LVM partitioning really help me here?  Last time, I put a pair of 3 TB spinners into an LVM, even though I only had about 1 TB of media files.  I thought this was the only way that Kodibuntu would present all my content in one location.  I am thinking about slowly replacing the spinners with SSDs as my budget allows.

(2) Has any Ubuntu user had success with the PCI-e boards that let you use NVM-e SSDs?  This would allow me to add smaller, less expensive (2 TB) SSDs and fit more of them into a machine, as my content increases.  Will Ubuntu recognize SSDs on this add-in board?  (The CPU/GPU has onboard video, so the PCI-e slot is free.  It might only be x8, but that's good enough for the add-in board I intend to use).

Please let me know any experience you have, especially with that add-on board......

Thanks in advance !

---

### Post by TheFu on 2020-12-26
lvm is useful, but has to be setup before it can be used. using lvm to merge multi-disk storage isn't needed. Modern media centers understand multiple partitions for each type of media and merge the views in the db and view from the db.

**pvmove** is handy when transferring to new storage. That's lvm.

Why replace cheap storage with expensive SSD storage? It isn't like media playback needs fast storage.
Consider that 4tb is $40-$70 and 2tb SSD is $170+; more than 2x the cost. Backups?

A case could be made for the OS and DB to use SSD storage. A huge media collection only needs 100G for those combined.

sorry,  don't know about addon ssd cards.  I only have 1 ssd per system here, for the OS, not media.

PCIe storage can only use x4 bandwidth today wth NVMe storage. The newest 2020 Ryzen motherboards have that, not the 2018 versions. Spend money where it matters. 4K video doesn't need ssd performance.

Now, if you edit and create 4k video  scratch space on SSD in RAID0 makes sense.

---

