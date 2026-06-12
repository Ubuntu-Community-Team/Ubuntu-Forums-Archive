---
title: "Master Boot Record (MBR) restore (XP)"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by roy20 on 2009-05-18
Hi All
I've installed Ubuntu as a dual boot on my Samsung NC10 Netbook and apart from a few glitches so far so good - all hardware got recognised immediately without any downloads or tinkering. Amazing !

Although I don't need to do this yet, I would like to know how I can restore the MBR that the Grub bootloader has overwritten, if necessary - the Samsung's re-load routine would do it but its a scorched earth policy - everything is wiped. In the past I would just use FDISK /MBR and I could do that with an XP version run from a flash drive using the recovery console but that would not be the Samsung's specific version. But it would do.

Any other ideas?

Roy

---

### Post by coffeecat on 2009-05-18
> **roy20 said:**
> In the past I would just use FDISK /MBR and I could do that with an XP version run from a flash drive using the recovery console but that would not be the Samsung's specific version. But it would do.

Any other ideas?

The mbr code for Windows is about 400 bytes of code, so I don't know about a Samsung specific version. Anyway, [this site]("http://www.users.bigpond.net.au/hermanzone/p18.htm") lists about a dozen ways of restoring the Windows MBR. Just be aware that one or two there are not well written up. For instance, the ms-sys method tells you to sudo apt-get install ms-sys. Which would be OK if ms-sys were in the repositories. :roll: If you follow the links, you eventually get to a download page for a ms-sys deb file.

Be that as it may, my favourite is SuperGrubDisk. I've repaired the mbr for Windows 7 on sda1 on one machine and XP on sda2 on another and both worked. And then I've used SGD to reinstall grub stage 1 to the mbr on both - just to prove to myself that it works. :p

SuperGrubDisk gets my vote. Add it to your box of emergency tools!

---

### Post by roy20 on 2009-05-18
Many thanks for the reply - I'll give SuperGrubDisk the once over asap !

Cheers, Roy

---

