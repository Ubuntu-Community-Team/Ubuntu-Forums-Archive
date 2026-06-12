---
title: "Doesn't boot past &quot;Grub ....."
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Meanderer on 2009-11-05
I'm new to Linux but I have had Ubuntu 9.04 installed for a few months on slave drive and win XP on Primary.
I burnt a 9.10 image disc and have installed a few times with reformatting option in installation to overwrite the whole slave drive. (sdb)
Supposedly all went well each time until I try to BOOT. It gets to when it says, searching to boot from, floppy, cdrom, drive 0 and then says GRUB and cursor just flashes after that and hangs.
I've spent two full days and nights reading, reading, reading and trying things (best way of learning of course) but I just can't find out how to set up this GRUB or GRUB2 to work.
During installation, I chose to boot from Master drive (not the drive with 9.10 on it) but it seems that is suppose to be ok to do.
Hope someone can help as I can only use the Live CD to work my PC and that takes so long to boot between tries. I'm out of time!!! :(

---

### Post by Mujaheiden on 2009-11-05
boot with the live cd and try with the instructions at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

just dont confuse yourself too much with the drives :)

---

### Post by Meanderer on 2009-11-05
Thanks but I had already solved the issue before I got back to see your reply. Although I now have Ubuntu 9.10 installed and booting on dev/sdb, I can't "see" my sda from "Places".
It showed in the List during the Grub2 install.
My original problem was due to the fact that I had been putting Grub2 on /dev sda BUT because that has my WinXP which is a NTFS formatted drive and Grub2 can't write to that. Hence I installed Grub2 on /dev sdb which is ext4 formatted and changed my BIOS to boot from IDE 1
So now I need to read more and find out why my sda can't be accessed like it could when I was using 9.04 and Grub 0.97

---

