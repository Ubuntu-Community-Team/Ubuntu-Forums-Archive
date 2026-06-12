---
title: "Impossible to boot from a Live USB that has been restores from a backup image"
date: 2017-12-05
forum: Hardware
---

### Post by blau2 on 2017-12-05
Hi,

I've been thinkering with this issue since long ago, and I don't see anyone experiencing the same trouble I have.

The thing is quite easy. I backup a live usb (I've tried either with a dd command or with Clonezilla as well) that boots from EFI and has a FAT32 partition with ISO images, and a ext2 partition casper-rw for persistent storage. Everything goes fine with the backup, the image is created, it is said to be fully "restorable".

If I restore the image on the same pendrive, everything runs smoothly, and I can boot from the restored pendrive.

The trouble comes when I try to restore the image to a new pendrive with more capacity, either with dd or Clonezilla. When analyzing the newly restored usb stick with gparted, I see a right FAT32 partition, and the other partition is there exactly with the same size of the original ext2, but it is shown as having an unkown file system. Boot-repair shows that there is a sde2 partition with a Linux system, but it reports that it isn't mounted and that it has an unkown file system as well.

I just can't understand how an image isn't restored exactly with the same configuration, partitions and information of the original one. Specially when neither the backup nor the restore process reports any error :confused:

Please, I'm in a dead-end. I do need some experienced help. Thanks beforehand :D

Blau.

---

### Post by sudodus on 2017-12-06
The method, that you use should work with a drive, that has an MSDOS partition table, alias 'MBR'. But if the drive has a GUID partition table, there is also a notion about the tail end, where there is/should be a backup partition table. This will not be correct after cloning to a drive with a different size. If the drive with the cloned copy is bigger than the original, it can be fixed with **gdisk**.

This problem is addressed by mkusb, when used for creating a USB drive from an image. There is also a small shellscript, that can fix it. See the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Expansion and imaging from a compressed image file](https://help.ubuntu.com/community/mkusb#Expansion_and_imaging_from_a_compressed_image_file)

[help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix)

---

### Post by blau2 on 2017-12-11
Hi sudodus,

First of all, thank you very much for your quick and detailed response. 

Unluckily, I've tried both mkusb and gdisk, but the thing didn't work. Finally, I decided to use the gpt-fix shell script and I got the message "The GPT seems fine or there is no GPT on /dev/sde" 

Any other clue on why I'm experiencing this issue.

Thanks again. 

Regards, 

Blau

> **sudodus said:**
> The method, that you use should work with a drive, that has an MSDOS partition table, alias 'MBR'. But if the drive has a GUID partition table, there is also a notion about the tail end, where there is/should be a backup partition table. This will not be correct after cloning to a drive with a different size. If the drive with the cloned copy is bigger than the original, it can be fixed with **gdisk**.

This problem is addressed by mkusb, when used for creating a USB drive from an image. There is also a small shellscript, that can fix it. See the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Expansion and imaging from a compressed image file](https://help.ubuntu.com/community/mkusb#Expansion_and_imaging_from_a_compressed_image_file)

[help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix)

---

### Post by sudodus on 2017-12-11
It seems there is an MSDOS partition table, where cloning should work from a smaller drive to a bigger drive. I have done it many times.

Please describe how you used mkusb, what commands you used, and how mkusb responded.

Did you use mkusb in order to clone from the dd image to the new drive?

Did you use Clonezilla in order to restore from the Clonezilla image to the new drive?

---

### Post by blau2 on 2018-01-14
I sudodus. I'm sorry not be have answered before, but it seems that I missed this email notification. 

I created the bootable live linux pendrive by following these instructions: 

Section "2. The ISO loopback method (advanced)" at [https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)

And then, in order to be able to have a live usb larger than 8GB, I followed these instructions 

Answer from "C.S.Cameron said: May 20th, 2013
Re: Persistent USB on windows 7 UEFI
Most good flash drives do have wear leveling, see link below. [...]" at [https://ubuntuforums.org/showthread.php?t=2108487&page=3&p=12656460#post12656460](https://ubuntuforums.org/showthread.php?t=2108487&page=3&p=12656460#post12656460)

To try to clone the live usb created as described above, I tried both: dd command from the command line, and clonezilla as well. None of them worked, and both had as a result a live usb that didn't boot. 

Thx again for your help and sorry for the unconscious delay. 

> **sudodus said:**
> It seems there is an MSDOS partition table, where cloning should work from a smaller drive to a bigger drive. I have done it many times.

Please describe how you used mkusb, what commands you used, and how mkusb responded.

Did you use mkusb in order to clone from the dd image to the new drive?

Did you use Clonezilla in order to restore from the Clonezilla image to the new drive?

---

### Post by C.S.Cameron on 2018-01-14
That method of creating a persistent flash drive stopped working with 14.04.

Nowadays many Bootable USB makers, (Startup Disk Creator, Rufus, etc), create a clone on an ISO9660 partition.

Basically any modification to the drive makes it unbootable.

If you want a flash drive with >4GB persistence **mkusb** is the answer, if you have access to Ubuntu to install it. It can also be run on a Live or Persistent USB.

Mkusb creates a FAT32 boot partition, an ISO9660 OS partition, an ext2 casper-rw partition and a NTFS data partition that can be used by Linux or Windows.

If you only have access to a Windows computer, YUMI will make a USB drive with persistence >4GB, but it works with large persistence files not partitions.

---

### Post by sudodus on 2018-01-15
I agree with C.S.Cameron, and suggest that you try mkusb.

---

### Post by blau2 on 2018-03-04
> **sudodus said:**
> I agree with C.S.Cameron, and suggest that you try mkusb.

Thanks sudodus, finally you both have helped me a lot to find out what was going wrong. I do really appreciate it!

---

### Post by blau2 on 2018-03-04
> **C.S.Cameron said:**
> That method of creating a persistent flash drive stopped working with 14.04.

Nowadays many Bootable USB makers, (Startup Disk Creator, Rufus, etc), create a clone on an ISO9660 partition.

Basically any modification to the drive makes it unbootable.

If you want a flash drive with >4GB persistence **mkusb** is the answer, if you have access to Ubuntu to install it. It can also be run on a Live or Persistent USB.

Mkusb creates a FAT32 boot partition, an ISO9660 OS partition, an ext2 casper-rw partition and a NTFS data partition that can be used by Linux or Windows.

If you only have access to a Windows computer, YUMI will make a USB drive with persistence >4GB, but it works with large persistence files not partitions.

Thanks C.S.Cameron, finally you both have helped me a lot to find out what was going wrong. I do really appreciate it! 

I have just one question left to find an appropriate solution for my needs. This thing that you say "That method of creating a persistent flash drive stopped working with 14.04", how would I be able to find a workaround for it? I guess an upgrade of my Linux release would solve the issue, but do I have to upgrade the pendrive I want to clone or the other pendrive with which I am executing the dd for the backup/restore? Which one of them is affected by the 14.04 limitation? 

Thx again. The community behind Ubuntu is what makes this distro really great.

---

### Post by sudodus on 2018-03-04
mkusb works with all current Ubuntu and Ubuntu community flavours (including 14.04 LTS).

I don't see the reason to stay with a method that does not work with 14.04 LTS.

Also, the only reasons to stay with 14.04 LTS would be that the newer LTS version does not work in your computer and that you have not the bandwidth to download a new iso file.

Otherwise I would recommend 16.04 LTS or if you have a new computer, 17.10.1 and soon (when released in April 2018) the new 18.04 LTS version.

---

### Post by C.S.Cameron on 2018-03-04
It is not the disk you are running dd from, any old version of Ubuntu should be able to use dd to clone a drive.
It is also not just the version of Ubuntu, some installers such as mkusb and YUMI will work fine with persistent partitions on current versions of Ubuntu, (YUMI will work with multiple ISO files and multiple casper-rw persistence files of unlimited size. So will mkusb, but it takes a bit of hacking. Multiple casper-rw partitions do not work).
Remember with a persistent install it is only the contents of casper-rw that is unique, the OS itself is locked in a read only squashfs file. You can copy the contents of a casper-rw file or partition using rsync.

If you want a bootable USB drive for long term use, there are advantages to doing a **Full** install to the USB, Faster boot, greater security, ability to update and upgrade, better use of disk space, ability to hibernate, less likely to go corrupt, easier to clone, proprietary drivers work.

A mkusb install can be used as a base for a Full install that works with BIOS and UEFI: [https://ubuntuforums.org/showthread.php?t=2385802&p=13743180#post13743180](https://ubuntuforums.org/showthread.php?t=2385802&p=13743180#post13743180)

---

