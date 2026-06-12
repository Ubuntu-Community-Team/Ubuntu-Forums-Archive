---
title: "ASUS K8V SE Deluxe + RAID"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by Herrscher on 2005-09-11
Hi community!

I got the following system specs:

[list]
[*]ASUS K8V SE Deluxe Motherboard (Socket 754)
[*]AMD Athlon64 3200+ CPU
[*]Onboard RAID 0 / 1 / 0+1 Controller Promise 20378 (2x SATA, 1x IDE)
[*]Onboard VIA VT 8237 RAID 0 / 1 Controller (2x SATA, 2x IDE)
[*]Radeon 9800 Pro 128 MB AGP
[*]Soundblaster Audigy 2 ZS
[*]2 x Hitachi 160 GB SATA @ Promise 20378 via RAID 0 (Striping)
[*]CD-RW and DVD-RW ATAPI @ VT 8237
[/list]

So I have actually a 320 GB RAID 0 drive under Windows XP Professional.
It works great.
I have much unused drive space however, so I'd like to install Ubuntu here also.

Is this possible with the above RAID configuration?

Some people say, that the Promise RAID is just emulated via a Windows driver.

And there are no Linux 64-Bit drivers at all for this RAID controller.

I'm remembering having read about a guy, who used the Linux LVM to construct an exact "copy" of the structure of the Windows RAID, so that it got usable under XP and Linux at the same time. The LVM did "emulate" the stuff that the Promise driver was doing under XP. No partitions got harmed.
However, it was too complicated for me at that time, and nowadays I can't find the link anymore.

Is this possible?

What would be the single steps to perform this without data loss?

---

