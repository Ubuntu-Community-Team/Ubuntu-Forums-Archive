---
title: "Converting to GPT"
date: 2010-08-12
forum: Hardware
---

### Post by X5-655 on 2010-08-12
I can't find a clear answer on this.

How can I convert my laptops partition to GPT, so I can install Grub2 to boot my laptop with EFI and not BIOS compatibility mode.  My laptop has EFI, and is a Compaq..  I'm running 64-bit 10.04..

I need this as easy as possible for someone who has never done this before..

[http://img.photobucket.com/albums/v395/Evilweredragon/partitions.png](http://img.photobucket.com/albums/v395/Evilweredragon/partitions.png)

[http://img.photobucket.com/albums/v395/Evilweredragon/gparted.png](http://img.photobucket.com/albums/v395/Evilweredragon/gparted.png)

That's the layout I have right now.

---

### Post by oldfred on 2010-08-13
I do not know if you can convert from MBR to gpt. Grub also has some issues with true efi which it sounds like they are fixing in Maverick.
grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Converting:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. may destroy all data per srs5694
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

### Post by srs5694 on 2010-08-23
My [GPT fdisk](http://www.rodsbooks.com/gdisk/) will do the MBR-to-GPT conversion; see the [Converting to or from GPT](http://www.rodsbooks.com/gdisk/mbr2gpt.html) and [A gdisk Walkthrough](http://www.rodsbooks.com/gdisk/walkthrough.html) pages of the documentation for details.

Converting from MBR to GPT is likely to be the easy part, though. Documentation on booting Linux using (U)EFI is pretty scant. I don't have a real (U)EFI system for testing, so I can't offer any first-hand advice on that score.

---

### Post by X5-655 on 2010-08-23
I tried to use GPT Fdisk, but it got so confusing..  In Windows it's a piece of cake, goto Disk Management, right click on the drive, and just select "Convert to GPT" and it's done all by itself.. But on GPT Fdisk I have to pick through everything manually, and in the end, I just gave up and found it not worth it.

Besides, I kinda gave up with Linux now after using it since Mandrake 7..  Too many bugs with my laptop that it's just not worth it anymore.

---

