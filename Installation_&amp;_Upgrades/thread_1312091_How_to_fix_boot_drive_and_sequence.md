---
title: "How to fix boot drive and sequence"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by monreveur on 2009-11-02
I have 3 hard drives in my computer:

[LIST=1]
[*]IDE/PATA drive as Channel 0 Master (1 EXT3 partition, bootable, empty) (/dev/sdc1)
[*]SATA drive as Channel 2 Master (1 NTFS partition, bootable, Windows XP) (/dev/sda1)
[*]SATA drive as Channel 3 Master, partitioned as follows:
[LIST=1]
[*]EXT3 partition, bootable, empty (/dev/sdb1)
[*]Extended partition (/dev/sdb2)
[LIST=1]
[*]EXT4 partion, not bootable, clean install of Karmic Koala (/dev/sdb10)
[*]Swap space (/dev/sdb11)
[*]Swap space (/dev/sdb5)
[*]EXT3 partition, not bootable, Jaunty Jackalope (no data) (/dev/sdb6)
[*]Swap space (/dev/sdb7)
[*]EXT3 partition, not bootable, Karmic Koala upgrade from Jaunty Jackalope (/dev/sdb8)
[*]Swap space (/dev/sdb9)
[/LIST]
 
[/LIST]
 
[/LIST]
I have the BIOS set to boot the above drives in this order: 3, 2, 1

Originally I had Windows XP on drive 1. It is now empty but I'm fairly certain that GRUB won't load if I take drive 1 out of the computer. At least this was the case at one point so I keep it. I'd rather remove it if possible.

I'm not sure how drive 3 got partitioned so oddly. The boot files (including menu.lst) are being read off /dev/sdb6. As usual, any update, upgrade, or clean install fails to work until I boot into /dev/sdb6 and fix menu.lst and copy the boot files. (Except I haven't even got to see the clean install because Jaunty won't read EXT4. I didn't see when or if I was given the option to use EXT4. Actually, I only did the clean install due to the several seconds that grub now turns off the video while booting /dev/sdb8. It seemed broken.) I really only want to keep /dev/sdb8 and it's matching swap space.

In summary:

[LIST]
[*]Remove the IDE drive completely.
[*]Delete all but /dev/sdb8 and it's corresponding swap space.
[*]I'd even like to fix the drive boot sequence in the BIOS.
[/LIST]

---

