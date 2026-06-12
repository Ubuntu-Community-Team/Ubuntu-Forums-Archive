---
title: "BOOTMGR is missing"
date: 2013-06-03
forum: Hardware
---

### Post by jimouris15 on 2013-06-03
Hi Forum 
I'm new here and i have a problem 
I have Asus Eee pc and i was using Backtrack but in the future i bored them and i think that its time to remove them 
I installed **[SIZE=3]GParted [/SIZE]**[SIZE=2]and i delete all the partitions and formatting with that way the hardware.
Backtrack said that this will take effect when i reboot the laptop.
i done it but it stucks in a black screen with a score lighting over and over again without a result.
Now when i try to make my netbook ubuntu with a bootable flash driver(I used the unebootin to bootable the flash driver)it appears that message [/SIZE][SIZE=3][B]BOOTMGR is missing 
                                                                                                                                                                                                    Press Ctrl+Alt+Del to restart  
[/B][/SIZE][SIZE=2]How can i make my netbook ubuntu and how can i fix the problem[/SIZE][SIZE=3]** BOOTMGR is missing? **[SIZE=2]
I will [/SIZE][/SIZE]appreciated that ;)

---

### Post by Bashing-om on 2013-06-03
[COLOR=#000000]jimouris15; Hi !

Try this:

[/COLOR]You will need a LiveCD/USB. Boot into the Live Environment and activate a terminal, key combo ctl+alt+t ;
Mount your OS partition:
```
sudo mount /dev/sda1 /mnt
```
Next, install GRUB2:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Make sure you understand the nomenclature, as in that sda = 1st hard drive, sdb = 2nd hard drive.
(Don't put a partition number in this command, just the HDD location a, b, etc.)
nomenclature: sda1 = 1st hard drives 1st partition, sda2 = 1st har drive 2nd partition. sdc7 =3rd HD 7th partition
Now unmount:
```
sudo umount /mnt
```

Making sure that grub (GRand Unified Bootloader) is installed onto the MBR of the drive that holds the ubuntu installation !
Re-boot into the install . (what is set in bios for the boot priority ??)[INDENT=2]
hope it is as easy as this [/INDENT]
[COLOR=#000000]
[/COLOR]

---

### Post by jimouris15 on 2013-06-04
Thanks for your reply.
Anyway the problem was in the usb because the usb was ntfs formatted.
when i formatted to fat32 the bootmgr wasn't there 
Do you think that my Asus eee pc 1005ha will keep windows 7 32bits?

---

### Post by Mark Phelps on 2013-06-04
> **jimouris15 said:**
> Do you think that my Asus eee pc 1005ha will keep windows 7 32bits?

Don't understand the "keep" part ... you said>  I installed GParted and i delete all the partitions and formatting with that way the hardware.
 which means you REMOVED the partition(s) containing Win7.

If that's the case, there is nothing there to "keep".

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]jimouris15; Hey;[/COLOR]

[COLOR=#000000]See Mark's last... I think it behooves us to look at your partitioning scheme and see what is on your disk; terminal commands FROM the live invironment : such that the install's partitions are not mounted.[/COLOR]
```

sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

```
[INDENT=2]
a tale will be told

[/INDENT]

---

