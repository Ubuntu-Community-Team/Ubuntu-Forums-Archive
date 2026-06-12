---
title: "xp is bullying my ubuntu ... help"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by shift_00 on 2009-03-20
hi to all,

well the story is about my laptop having linux ubuntu as its only operating system, then at work i was asked to work on a component that utilizes serial ports on windows, and since i have an old machine, i thought i can set xp on that one, and resize my partitions to allow a 10G for a quick xp installation.

and so i started, booted the xp cd into my box, and started formatting, it mentioned something about it will mark the "undefined" partitions as inactive and that i can activate them later from disk management, usually microsoft isn't very honest about anything that i can do "later", but i thought what the worse can happen.

so it happenned, my ubuntu is obsolete, it is there, but the activate button is deactivated, i can only reach my old partitions via shell loaded by the ubuntu cd, so i got frustrated, and i deleted the newly added xp partitioned, and i installed another ubuntu "yes now i have dual boot ubuntu systems, yaay".

now my dear sirs and madams, i want to install an xp version without having to format the whole box, because my ubuntu is updated and tweaked and given it was my first real migration to linux programming, i'm kinda emotionally attached to it. "i'm still a linux noob btw"

any help?

---

### Post by Partyboi2 on 2009-03-20
You could boot a ubuntu live cd and use gparted (System>Admin>Partition Editor) to shrink down your ubuntu partition if you have not already done so and create a ntfs for installalling windows. Then install windows using the ntfs paritition your created for it. Once windows is installed boot the ubuntu live cd again and follow [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub.

---

### Post by Anthon on 2009-03-20
Since XP doesn't know about Ubuntu I don't think it will ever make 
boot entry without further action.

After (re-)installing XP, try to boot Ubuntu from CD and then use grub and install the bootloader to boot from your original Ubuntu partition.

After that edit /boot/grub/menu.lst of your original Ubuntu partition and add something like:
title		Microsoft Windows XP Professional
root		(hd0,1)
chainloader	+1

You might have to do some saving of the XP bootsector, I am not sure about that. I have normally started with XP and then install Ubuntu.

The IMHO fail safe alternative is to:
1) backup your original Ubuntu partition after booting from CD. (tar cvf /media/USBDRIVE/ubuntu_good.tar /)
2) install XP
3) install Ubuntu from CD in the partition of the original Ubuntu
4) check you can boot XP and Ubuntu from the grub menu
5) make a copy of the /boot/grub/menu.lst to the USBDRIVE
6) boot from Ubuntu CD, clean out the Ubuntu partition and restore from /media/USBDRIVE/ubuntu_good.tar 
7) Update /boot/grub/menu.lst with the information for booting XP

Depending on your partition sizes (and % usage) it will take some time to do the copying, but you don't have to do much interactively.

---

### Post by dandnsmith on 2009-03-20
*You might have to do some saving of the XP bootsector, I am not sure about that. I have normally started with XP and then install Ubuntu.*

If you want to restore the grub bootloader on the MBR, then you don't need to worry about XP bootloader - the chainloader etc is sufficient.
It's different if you want to boot linux from the XP bootloader arrangements.

---

