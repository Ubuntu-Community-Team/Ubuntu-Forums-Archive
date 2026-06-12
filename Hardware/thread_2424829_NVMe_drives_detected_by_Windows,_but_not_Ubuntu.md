---
title: "NVMe drives detected by Windows, but not Ubuntu"
date: 2019-08-15
forum: Hardware
---

### Post by pheebsh on 2019-08-15
Hello all,

I have a batch of NVMe hard drives that are not detected by Ubuntu, but they show up in Windows.

Specifically, I have Toshiba KXG50ZNV1T02 (1TB) NVMe M.2 drives.
I'm using an HP workstation running W10 64-bit.
My Linux setup is Ubuntu 16.04 LTS running on an NVIDIA Jetson TX2 (ARMv8) attached to a developer kit carrier board.
Neither the workstation mobo nor the carrier board have an M.2 slot, so I'm using a PCI-E adapter board (StarTech PEX4M2E1).

I started with a batch of about 40 drives. 60% of them were detected successfully in both operating systems.
The remaining 40% are detected by Windows only.

I've tried deleting all partitions, formatting as exFAT and as NTFS. None of these routes have resulted in success.

I'm at a loss for why some of these drives work in Linux and some don't, while all work in Windows.

Thanks for your time.

Phil

---

### Post by yancek on 2019-08-15
I would expect that if you have the windows proprietary filesystems on the drive that they would work on windows.  Generally, an ntfs formatted drive should be recognized by an Linux OS.  Few Linux systems have support for exfat by default so additional software would be needed.  Are the drives recognized if you have a Linux filesystem on them?  Are these new drives or have you had them attached to a booted windows system, the ones that are not recognized?  Are the drives from the same manufacturer?

---

### Post by pheebsh on 2019-08-15
> **yancek said:**
> Are the drives recognized if you have a Linux filesystem on them?  Are these new drives or have you had them attached to a booted windows system, the ones that are not recognized?  Are the drives from the same manufacturer?

As far as I can tell, the drives have Windows partitions. And I don't currently have (or know of freeware) that can create Linux partitions in Windows.
All drives are the exact same Toshiba drive.
The drives are not new. And, honestly, I can't speak for their state. Some seem to have files on them. Some are unformatted.


Thanks for the response. I just put a Ubuntu Live CD into the workstation PC and the drive appeared, but would not mount.
In fact, it provided me with a (hopefully) very useful error message. Here's a snippet of the error:
"Disk contains an unclean file system (0,0). Metadata kept in windows cache, refused to mount."
and
"NTFS partition is in an unsafe state. Please resume and shutdown Windows fully."

Bear in mind, I was properly shutting down Windows each time I tested a drive,
but perhaps reformatting them again as NTFS and shutting down might do the trick.

---

### Post by pheebsh on 2019-08-15
The latest:

Using "ntfsfix" on the partition allows it to be read from the Ubuntu Live CD on the workstation,
but the drive still doesn't show up at all when I plug it into the NVIDIA TX2.

---

### Post by yancek on 2019-08-16
> NTFS partition is in an unsafe state. Please resume and shutdown Windows fully.

Very common error.  I expect you are using windows 10 which by default hibernates rather than shutting down.  This error is shown when trying to mount a windows partition from Linux that is hibernated so if these drives weree attached to  windows 10 machine, that might be the problem.  To avoid this, windows hibernation must be off and FYI, hibernation will be turned on again without notifying the user during updates.

---

### Post by Autodave on 2019-08-16
When you choose to shut Win down, it actually does not shut down.  You need to go into the BIOS and shut *fast boot* off.

---

### Post by CatKiller on 2019-08-16
> **Autodave said:**
> When you choose to shut Win down, it actually does not shut down.  You need to go into the BIOS and shut *fast boot* off.

Windows' fast boot and the BIOS' fast boot are different things. It's the Windows setting that makes drives useless, and it's the BIOS setting that stops you getting back into the BIOS.

---

