---
title: "Super Hard Drive Array!"
date: 2009-03-11
forum: Hardware
---

### Post by Mr.Macdonald on 2009-03-11
I have recently scrapped my old server, and wanted to use the parts for a cool project.

I have 2 IDE hard drives and 1 IDE CD/DVD RW drive.

Can I chain them with slaving IDE ribbon cables (all hard drives and CD drive). If this is possible, what order would I want the drives in, by attributes of drive (drive speed, size)? Would enslaving the drives slow the read/write times.

Can Partition a drive into 4 equal parts, then software RAID them together. Would this give a significant speed benefit?

Can I copy CD's by reading on cd drive and then directly writting to the other? "dd if=/dev/cdrom0 of=/dev/cdrom1"?

Can I write one image to two CD's at a time? "dd if=image of=/dev/cdrom*"

If I had two copies of a CD, could I software RAID my CD's together? Would I get a significant speed benefit?

Finally, if I were to uses these hard drive as external drives accessed via USB, which is the limiting component USB or Hard Drive? (5400 RPM)

---

### Post by madverb on 2009-03-11
> **Mr.Macdonald said:**
> I have recently scrapped my old server, and wanted to use the parts for a cool project.

I have 2 IDE hard drives and 1 IDE CD/DVD RW drive.

Can I chain them with slaving IDE ribbon cables (all hard drives and CD drive). If this is possible, what order would I want the drives in, by attributes of drive (drive speed, size)? Would enslaving the drives slow the read/write times.
**Don't put HDD's on the same ribbon as an Optical Drive. HDD's tend to use IDE80 cables and Optical Drives only need IDE40 ones.**

Can Partition a drive into 4 equal parts, then software RAID them together. Would this give a significant speed benefit?
**there is no benefit to this. i'm not even sure if it is possible.**

Can I copy CD's by reading on cd drive and then directly writting to the other? "dd if=/dev/cdrom0 of=/dev/cdrom1"?
**Yes. It's called 'on the fly'**

Can I write one image to two CD's at a time? "dd if=image of=/dev/cdrom*"
**I'm pretty sure that is possible.**

If I had two copies of a CD, could I software RAID my CD's together? Would I get a significant speed benefit?
**I don't think that is possible either.**

Finally, if I were to uses these hard drive as external drives accessed via USB, which is the limiting component USB or Hard Drive? (5400 RPM)
**USB**

Peace

---

