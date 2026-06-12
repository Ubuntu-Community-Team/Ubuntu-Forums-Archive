---
title: "Keeping bios settings"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by beacon on 2009-10-13
I have two hard disks, with three Linux distros installed. I am also trying to get at least one of those on a flash drive from which I can boot. I am stymied most of the time, because my bios settings keep changing. I try to get the booting sequence as USB flash drive, CD/DVD, then Sata. I try to save those settings before exiting, but the next time I boot, they have changed position, and in some cases, even the names have changed. Can anyone explain how I can make changes that will last?

---

### Post by wilee-nilee on 2009-10-13
> **beacon said:**
> I have two hard disks, with three Linux distros installed. I am also trying to get at least one of those on a flash drive from which I can boot. I am stymied most of the time, because my bios settings keep changing. I try to get the booting sequence as USB flash drive, CD/DVD, then Sata. I try to save those settings before exiting, but the next time I boot, they have changed position, and in some cases, even the names have changed. Can anyone explain how I can make changes that will last?

So make sure you document what changes your making in bios in case you make a mistake. generally hitting f10 after adjusting is the save. Be careful with bios general adjustments can generally be fixed but a improper flash can brick it altogether.

I think nobody has answered you yet due to you not describing what exactly you have been doing in bios, a exact point by point description will get you answers. I assume that you are familiar with hitting f12 to choose the boot from, which if your going to be cycling from HD boots to usb boots is a better option, maybe.

---

### Post by beacon on 2009-10-13
I. Thank you. Obviously I was not as clear as I had thought. In the bios when I boot normally (Ubuntu) I get the following: (1) First boot device: SATA: 3M-Maxtor; (2) Second boot device: CD/DVD and (3) usually but not always, Nvidia boot ag.

Under hard drives, I have (1) Sata: 3M-Maxtor and (2) HDD: PS-IC35L12

II. When I try to boot from a USB flash drive (Puppy) I get (1) SATA: 3m-Maxtor; (2) HDD: PS !C35L12; (3) USB: Kingston Drive. The hard drives are listed as (1) Sata (2) HDD (3) Kingston D. If I change the order so that Kingston D is first in both instances, the order is no longer there the next time I boot.

III. I also have another USB stick, and when it is inserted, I get the same order for the boot sequence, and for hard drives I have (1) Sata ((2) HDD (3) USB Sandisk Cr

I am puzzled first of all why the sequences are different, and why when I change them, they don't stay that way. I do exit with f10 which is supposed to save the changes but does not. I also know about f12 but don't really need it, since when I boot as in the first paragraph, I am given a list of the three distros on my hard drives, and I can choose from which to boot. That, of course doesn't help with USB sticks.

---

