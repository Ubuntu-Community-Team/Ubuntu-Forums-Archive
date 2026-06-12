---
title: "Can't copy image to a fat32 partition due to access permissions - Please help!"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by gavaiken on 2006-11-23
Hi, I have recently installed UBUNTU, i'm trying to install another image to a different partition on the same SATA II hard drive.

My machine:
Intel Core Due E6300 @ 1.86
1024MB DDR667 Corsair Memory 
2 x 250GB Sata II Seagate Hard Disk 
ConRoeXfire-eSATA2 - Motherboard 
Intel Extreme Graphics onboard
ATI Radeon X1600PRO 512MB - Pci-e Slot

Hard Drive 1(HD1): 4 Partitions, 
Partition 1 - Vista 80gb NTFS Primary
Partition 2 - Ubuntu 80gb EXT2 Primary
Partion 3 - Linux Swap 400 MB LINUX SWAP
Partion 4 - Empty FAT32 Primary

Hard Drive 2(HD2): 1 partition Windows XP professional

So i tried the command

dd bs=1048576 if=./image.img of=/dev/sda4 (as i have been instructed but the website i got the image from.)

from the folder containing the image(on a usb hard drive) and I get an error message
"You do not have permission to access this disk" or something similar 

when i go to /dev/sda4 and right click it says "You are not the owner" any tips?!

I have tried mounting the drive to a folder and this works fine but then when i use the command given above and point it to the folder it says

"/media/windows/ is just a folder" or similar.

I guess i just don't know enough about this dd function, i tried searching for it but found nothing helpful, it appears that for this method to work it must be pointing to an actual drive which for some reason i dont have permissions to.

It's a bootable image that i'm trying to install,

Thanks,
Gav

---

### Post by RAOF on 2006-11-23
The **dd** command does a binary copy from something-readable to a device.  It can't write to a place on a mounted filesystem, because just binary writing to space on the disc would destroy the filesystem - it wouldn't update all the information the filesystem uses to track where files are, etc.

Also, you'll find that /dev/sda4 will be owned by root (the super-user, capable of anything), and pretty much no-one else will be able to do anything to it.

Running **dd** through **sudo** will temporarily give dd root priviledges, allowing it to write the to /dev/sda4, like this:
```
sudo dd bs=1048576 if=./image.img of=/dev/sda4
```

Be **extremely** careful with dd, and sudo.  It will **absolutely unrecoverably** destroy **all data** on the partition you're writing to **as soon as it starts**.  Be absolutely 100% sure of your command line before hitting enter!

Incidentally, this will not copy the image onto the FAT32 partition.  This will **replace** the FAT32 partition with the contents of the image file.

---

