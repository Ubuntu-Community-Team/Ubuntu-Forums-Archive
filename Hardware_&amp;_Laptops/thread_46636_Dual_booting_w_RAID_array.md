---
title: "Dual booting w/ RAID array?"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by Sn1pe on 2005-07-05
I currently have Windows 2000 installed to a Raid0 array of 2x Raptors.  My linux partition is part of an IDE drive that I put in for more room.  I have been booting by changing the boot order in the bios.  How would I go about setting up grub to allow booting win2k on the raid array as an option?

---

### Post by alastair on 2005-07-05
You might be out of luck - or at least in for plenty research and some hacking. It depends on what type of "RAID" array - does Linux see it (seperate disks or RAID?) when booted? The likelihood is that Windows has special "RAID" drivers that let it see/boot the RAID device - Linux might not have. You would have to check your motherboard/RAID manufacturer.

---

### Post by neurosion on 2005-07-05
[QUOTE=Sn1pe]I currently have Windows 2000 installed to a Raid0 array of 2x Raptors.  My linux partition is part of an IDE drive that I put in for more room.  I have been booting by changing the boot order in the bios.  How would I go about setting up grub to allow booting win2k on the raid array as an option?[/QUOTE]
I have a similar setup and am able to dual boot with no problem.  Here's the way I've got it set up in Windows XP:

[BIOS boot order is IDE drive (Linux + GRUB), Windows array, IDE drive]

```
title Windows XP Professional
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```
This is on an Asus A8V, so the RAID in question is secretly a software RAID under the covers.  If you've got a real honest-to-God hardware RAID (which, if you're running off your motherboard, is unlikely) the procedure may be different.  Give this a try regardless.

Comments:

[list]
[*]rootnoverify tells GRUB "Trust me, it's bootable"
[*]you MIGHT have to do rootnoverify (hd1,0); I haven't needed to, but it seems most examples on the 'net include the partition number
[*]the map commands tell GRUB to internally remap the boot order (Windows won't boot if it's not first in the boot order)
[*]not sure what makeactive is for, but I think it speaks for itself
[*]chainloader +1 tells GRUB to relinquish boot responsibilities to the Windows boot loader
[*]I've also had success with skipping the makeactive step and adding a "boot" command to the end[/list]
Hope it helps.

-- Russ

---

### Post by Sn1pe on 2005-07-06
Thanks man!

```

title           Windows 2000 Professional
rootnoverify    (hd1,0)
map             (hd0)   (hd1)
map             (hd1)   (hd0)
makeactive
chainloader +1
boot

``` 

Works like a charm, this community is great man!

---

