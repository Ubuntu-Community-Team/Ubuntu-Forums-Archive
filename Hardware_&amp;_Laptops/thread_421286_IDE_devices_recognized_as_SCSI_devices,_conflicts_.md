---
title: "IDE devices recognized as SCSI devices, conflicts with USB storage.."
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by oleoleole on 2007-04-24
I have 1 SCSI drive, 3 IDE drives, and one memory card reader with 4 slots.

Im not using UUID as recognition for drives, because it sometimes corrupt somehow and cant boot. So I need to modify fstab with a Live-CD and then edit in grub to /dev/sd*

But the problem is, after upgrading to Feisty all my drives have turned to be SCSI devices. Its okay if I disconnect the card reader.. but if its connected, it will be assign the first drive letters, /dev/sda, /dev/sdb, /dev/sdc and /dev/sdd. My SCSI drive will then be assigned as /dev/sde instead of /dev/sda. On this causes the system not to boot.

When it comes to my normal IDE drives, I cant use hdparm anymore, because its not made for SCSI devices. IDE devices is assigned as /dev/sdf, /dev/sdh and /dev/sdg.

And my DVD/CD-burner is assigned as /dev/scd0.

I dunno, but maybe its kind of better to "emulate" or what it does to SCSI devices, and hdparm would be useless anyway. But the annoying thing is about the memory card reader that gets the drive assignments first.

---

