---
title: "Can't burn - pioneer 106 not recognized!"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by barb3tta on 2004-12-29
Hi all!
I installed ubuntu on my system few days ago...
I'm triyng to solve some problems, but I can't figure out what ind of problem is the following:
Ubuntu can't see my DVD recorder Pioneer 106, even in the device manager it lists only the DVD reader (hdd), but not the pioneer (hdc).
Quite strange, uh?
I tried to recompile the kernel, but nothing happens... is there some way to solve this situation? some module to add?

thanks in advance!
bye
barb3tta

---

### Post by hardcandy on 2004-12-29
First I would check my connections to the Pioneer and make sure it shows up in the bios check during a reboot.
Also, is the jumper on the Pioneer set correctly for Master (if it is on the same channel as the /dev/hdd, it should be set for master via the jumper).

---

### Post by barb3tta on 2004-12-29
[QUOTE=hardcandy]First I would check my connections to the Pioneer and make sure it shows up in the bios check during a reboot.
Also, is the jumper on the Pioneer set correctly for Master (if it is on the same channel as the /dev/hdd, it should be set for master via the jumper).[/QUOTE]
the dvd recorder works perfectly under winXP in the same system!
The BIOS recognize it correctly...
The jumper is set to master...

Dunno what to do!!!!

bye

---

### Post by hardcandy on 2004-12-29
> the dvd recorder works perfectly under winXP in the same system! 
That would have been something important to include in the original post, perhaps a review of "How to post questions" would be called for.

Since we know the device shows up in WinXp and in the bios, and the other device shows up correctly, let's look at the /etc/fstab file. Compare how the two dvd/cd devices, hdd and hdc, are listed. Is there any difference? If so, perhaps try changing the hdc entry to reflect the hdd entry-except the dvd reader needs UDF listed as a flile system type. If you are unsure, post a copy of the fstab file.

---

### Post by barb3tta on 2004-12-29
[QUOTE=hardcandy]That would have been something important to include in the original post, perhaps a review of "How to post questions" would be called for.

Since we know the device shows up in WinXp and in the bios, and the other device shows up correctly, let's look at the /etc/fstab file. Compare how the two dvd/cd devices, hdd and hdc, are listed. Is there any difference? If so, perhaps try changing the hdc entry to reflect the hdd entry-except the dvd reader needs UDF listed as a flile system type. If you are unsure, post a copy of the fstab file.[/QUOTE]
Sorry if I didn't post all the informations.... I thought it was obvious that the recorder worked perfectly before...

hdc and hdd are identical in the fstab file, but /dev/hdc doesn't exists...

Even dmesg doesn't show any "hdc" device....

I've added ide_generic and ide_cd in the kernel, things are still the same...

bye

---

### Post by hardcandy on 2004-12-29
OK, let's try turning off ACPI since it will interfere with IRQ assignments sometimes. Add "pci=noacpi" to the kernel boot line. This will let Linux assign the IRQ's instead of ACPI. 
The other thing I would suggest is to try with  the kernel  configured with SCSI support, scsi cd support, generic SCSI device support and IDE-SCSI emulation, and without ATAPI (IDE) CDROM drive support.

---

