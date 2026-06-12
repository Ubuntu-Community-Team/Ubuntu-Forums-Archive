---
title: "SATA Hard Drive Errors"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by Didjit on 2006-10-18
Brand new PC and I'm getting I/O errors on a Segate Sata Drive.

Oct 18 19:28:16 linuxboxamd kernel: [18829.488127] ata1: error=0x40 { UncorrectableError }
Oct 18 19:28:18 linuxboxamd kernel: [18830.661869] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Oct 18 19:28:18 linuxboxamd kernel: [18830.661871] ata1: status=0x51 { DriveReady SeekComplete Error }
Oct 18 19:28:18 linuxboxamd kernel: [18830.661874] ata1: error=0x40 { UncorrectableError }

Is it possible this is software related w/the Sata Drivers? Running Dapper 64bit, but I played in Edgy and received the same results. 

Suggestions?

Didjit

---

### Post by kidders on 2006-10-18
Hi there,

This is a nasty one :-( Have you checked your cables? It may simply be that your power cable or I/O cable is loose or faulty. At least I *hope* it's that simple.

I have a few hard disks that I leave sitting on top of my PC. Whenever I hit one a hard knock (causing the cables to wobble), I see errors like yours in my dmesg.

---

### Post by rbmorse on 2006-10-19
I had that happen to me when I set the BIOS to run SATA in AHCI mode under Dapper. Turns out AHCI is broken in the 2.6.15 kernel.

Two things you can do, both work: 1) check you BIOS settings and make sure the SATA mode is set to IDE, or, 2) Install the 32-bit Edgy beta where SATA as AHCI works fine. Dunno what is going on with Edgy 64.

---

### Post by Didjit on 2006-10-19
> **rbmorse said:**
> I had that happen to me when I set the BIOS to run SATA in AHCI mode under Dapper. Turns out AHCI is broken in the 2.6.15 kernel.

Two things you can do, both work: 1) check you BIOS settings and make sure the SATA mode is set to IDE, or, 2) Install the 32-bit Edgy beta where SATA as AHCI works fine. Dunno what is going on with Edgy 64.

Crud! I was hoping this was a hardware issue, since a new drive from HP is in the mail.... I do not have those bios settings.

I have been playing in 2.6.18 and see the same errors, so it must be bad blocks that occured during a write. I did run e2fsck. 

Any way to fix the drive or are the blocks damaged beyond repair??

Didjit

---

### Post by kidders on 2006-10-19
Hey again,

If you think you might have some bad blocks, the best thing to do is flag them, so they won't be used. For instance, you might do **fsck.ext3 -c ....**

If you *do* turn out to have some, you should probably think about scheduling repeat checks every now and then, to keep the bad block list up to date. Once every few weeks at 3am, maybe?

---

### Post by rbmorse on 2006-10-19
Turns out that particular set of errors has several causes, including drive hardware, so maybe it wasn't a AHCI problem after all.

---

