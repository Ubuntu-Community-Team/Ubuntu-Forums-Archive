---
title: "Grub error 18"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by marsian on 2005-06-29
Hi,
I am having a problem with Grub on my old K6-2/500 pc: whereas all was working fine since weeks, when I boot Hoary this morning Grub reported an ERROR 18. I've read in others threads that it's because the boot partition is beyond the limit reachable by the bios... but for sure it was working yesterday and I've not changed anything in the system...
Any idea ? (or solution, that would be even better  :wink: )

---

### Post by Burkey on 2005-06-29
[QUOTE=marsian]Hi,
I am having a problem with Grub on my old K6-2/500 pc: whereas all was working fine since weeks, when I boot Hoary this morning Grub reported an ERROR 18. I've read in others threads that it's because the boot partition is beyond the limit reachable by the bios... but for sure it was working yesterday and I've not changed anything in the system...
Any idea ? (or solution, that would be even better  :wink: )[/QUOTE]
 It is not only because the partition is past the logical limit, it can also be that the partition is damaged, has been moved or deleted.

I had the same problem when I changed some partitions on my hard drive under windows, for my case I had deleted the Hoary partition to facilitate a few things, and it was all good after I re-installed Hoary.

Are you dual booting?  Or some info on your partition setup.

another thing to bear in mind is if your CMOS battery has gone flat or settings have changed in CMOS then the hard drive might appear differently to it did before.

---

### Post by marsian on 2005-06-29
I will check the CMOS battery.

Here are some details regarding my configuration, maybe it can help:
The primary master disk is partitionned and Windows 98 and Ubuntu are installed on it:
hda1 => Windows 98
hda2 => /boot
Grub is located in the MBR.
When I choose "Windows" in the Grub menu, the Windows 98 session starts without problem (thus it seems that the HDD is well recognized by the BIOS, isn't it ?),
when I choose "Ubuntu", as I said, an ERROR 18 is reported and I'm asked to press any key to continue... when doing that, the Grub menu is displayed again.

---

### Post by Burkey on 2005-06-29
Well, I am certainly no expert, but yeah, sounds like the HDD is working ok, which makes me think there is just a problem loading Linux off it's partition.

If you boot off a LiveCD, then check your boot partition and see what is in the Grub menu.lst file, verify the kernel exists and all.

You could possibly re-run grub and get it to setup the files again for you, or as I said check the menu.lst.

You mention hda2 is /boot, what is your / partition?  I think Ubuntu normally sets these up on the same partitions doesnt it?  How big are these partitions?  Check the LBA settings in particular as you may still have an incorrect setting there (if the battery is flat or CMOS re-autodetected the Hard drive) This would mostly be a problem if the partitions are over 8Gigs and on older mainboards to my knowledge.

---

### Post by marsian on 2005-06-30
OK, tanks to your advices I've solved the problem.
In case it can help anyone else, here is the reason of the problem:
The BIOS parameters were still set for a previous 6GB HDD (the one I was using before installing Ubuntu) and not for the current one (13GB)...

What I can't understand is how my system was able to run properly in the past weeks with those wrong settings !?!...

---

