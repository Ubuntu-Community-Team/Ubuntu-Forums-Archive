---
title: "How to backup/clone XP to...NTFS"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by attilab on 2009-10-09
I am seeing to many explanations, don't know which way to go, pls need a first hand experience/advise:
1. Asus C90S barebone, HDD fresh formated w/ FDisk, 3 partitions before install, C and D and RAW (empty)
2. XP (installed first) on sda1 (C:) and sda5 (D:), both NTFS, all my programs were installed to both C and D !
3. ubuntu 8.10 (GNOME 2.24.1 installed second) and will stay here some time because the 9.x screw up some drivers, sda6 / and sda8 /home
4. I want to create an backup image file for XP C and D partitions and the MBR dual boot , save it to external HDD (will be NTFS). I am just gesing the image file shall be easier to maintain that a bunch (thousends) of files/folders in archive file? 
5. in case I need it just dump it back (recover) to C and D and perhaps to maintain the dual boot. my guess this not gonna work just like that with XP so I could eventually quick FDisk the C first. I am expecting that this "cloning" will be to the same size HDD and same hardware on my laptop.
This again shall be faster and painless than 24 hour effectively installing my software (and still not done yet).
6. I am not good with terminal and the linux terminology, pls show/advise me the easy to follow steps.

---

### Post by hal10000 on 2009-10-09
You can install partimage and use it from your ubuntu system to make an image (clone) of your ntfs partitions. It's a text based software, but with a gui and it's easy to use.
Backup of a ntfs partition will give you a warning, but you can ignore it, i never had any problems cloning ntfs patitions.

Or you might download and burn a clonezilla live-cd, it is also based on partimage, but has more capabilities. When you boot the clonezilla live-cd, you can also make images of your ubuntu system.

If you search in the repositories you might find other backup-software, but i suggest one of the two mentioned.

---

### Post by attilab on 2009-10-09
my main concern is, me to be able to store the image and read back from external NTFS HDD? talking about 30 or so Gb image file (C and D drive).

---

### Post by hal10000 on 2009-10-09
I think if you have ntfs-3g, which provides write-access to ntfs partitions, you can use clonezilla  to to save your images to a ntfs partition (but i'm not sure).

---

### Post by attilab on 2009-10-10
thanks a lot, I made it.
Clonezilla worked fine, after several runs over menu all looked straight forward. I've made the image of the complete XP installation, from my C and an other from D drive (these are actually physical devided partitions before XP)
What shall I expect at the time of the "restore"? the dualboot will be there on the primary partition (sda1) or I shall learn how to make it when I need it again?

---

### Post by alexandermdevereux on 2009-10-10
clonezilla will reinstall grub and the drive will still be bootable. I recommend learning grub commands just in case. If you need to reinstall grub later you can use the xp recovery console (press r at menu) and run fixmbr. If fix mbr doesn't work then type help and chose the closest one. These commands will overwrite the mbr but grub can still be installed.

---

### Post by attilab on 2009-10-11
> **alexandermdevereux said:**
> .....clonezilla will reinstall grub and the drive will still be bootable.... 

reinstall....does it mean that it will place it back at recovery? (when I copy back the C drive) or I will need to re-install it back? from the menu...I didn't got to that point and what later -better.

---

