---
title: "Intermittent Grub Appearance"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by benhall on 2007-07-28
I'm having an odd problem with my new system. Its a HP t3545, AMD X2 3800+ with a SATA drive for windows and an IDE drive with Ubuntu (taken from a previous machine, but with feisty reinstalled over the original / contents).  The problem is that the grub boot menu doesn't always appear- sometimes it boots straight into windows, sometimes it goes to the grub menu. On neither occasion does an error message appear. Grub is installed on the IDE drive, and the BIOS indicates that this boots first. Other posts in the forum to do with grub all seem to have some sort of error message- any help would be much appreciated!

---

### Post by benhall on 2007-07-28
Ok, I've done a bit more troubleshooting and it might be hardware based. The problem only appears to present itself when booting the first time after the power is turned on at the wall- if I restart it doesn't happen, and looking at the bios boot menu on first boot (after power on) the ubuntu drive isn't seen(!).

If this is the case, a simple fix would be to edit the windows boot menu so that I could redirect it to the second hard disk after startup. Can anyone offer advice on editing the Windows XP boot menu? Alternatively I could overwrite the windows bootloader with grub, but that would be a less preferred option. Thanks in advance!

---

