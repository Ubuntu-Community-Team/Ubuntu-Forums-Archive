---
title: "help installing ubuntu (studio) on an existing FAT32 firewire partition ?"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-06-19
hello all

i have this 1To firewire 800 drive that I use to store mac os X dual boot systems, and date that i desperately need to preserve.

now this drive also has an empty 32Gig FAT 32 partition, as well as another 10 Gig FAT 32 partition, that i would like to use to install ubuntu studio (32Gig partition) and the SWAP (onthe 10 gig one)
yet i would like to be sure to protect the other exisiting partition ( 3 others, in NTFS+) and install in the right place, and not mess up.
the installer is a little confusing, could somebody kindly help me do this install while protecting my data etc on the other partitions ? i really need to make sure i'm installing ubuntu studio and its swap in the right place, yet this installer doesn't seem designed for installing on pre-existing partitions like this

thanks greatly for your help

ben

---

### Post by dstew on 2009-06-19
You cannot install Ubuntu onto a FAT32 file system. You would need to re-format the root partition as ext3 or ext4. The swap partition does not need a file system, but you might have to delete the FAT32 file system there in order for it to be used as swap. To delete the file system, you might need to delete the partition, then re-create it as unformatted space, designated "use as swap".

With a complicated partitioning problem, I like to create the partitions I will use before installing, using the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). It just feels less intimidating when, during the installation, the partitions are already there. Use "Manual Partitioning" during installation. Even though the partitions are there, you still may need to format them, and you will need to designate at least a root partition (mount point '/', without the quotes) and designate another partition as "use as swap".

---

### Post by bjaz on 2009-06-20
thanks for this answer.
I had actually initially created the partitioning system using Gparted, but thought that a FAT32 file system was needed. I'll change the root partition to ext 3 or 4 and delete the space i intended for swap, recreated as free space for swap.

maybe the manual partitioning will become clearer, as with the current erroneous partitioning setup i had it wasn't really clear wether i could choose the intended partitions

b

---

### Post by bjaz on 2009-06-20
ok, thanks to your help, i'm almost there.

the partitioning went well, i have 10gig swap partition (sdb2), and a 30gig ext4 / root partition (sdb6) on which in did an install, and my other partitions with the 2 mac os systems and the storage space are fine.
yet i can't seem to be able to install the GRUB bootloader anywhere on this drive. and hence can't boot into the system

i get a fatal error.
it's a firewire 800 drive (esata enclosure from what i remember), and there's never been an issue installing bootable systems from it, using a macbook pro
yet here i get a fatal error. i've tried creating a new bootable partition in ext4 format (sdb7), on which to install the GRUB, and playing around with the different options to no avail.
when i choose /dev/sdb7 or others as install points, it won't install. i would have liked to install this on one othe existing partitions on the external drive.
  

what should it try ? i don't have a floppy disk reader on this machine.

thanks

ben

---

### Post by bjaz on 2009-06-20
edit - i finally removed the sd7 partition.
i've tried installing the GRUB on sdb1, which is an EFI boot disk, and on others, but it doesn't seem to work. i've been trying to read up on the subject but it's taking me in multiple directions.
the sdb6 install worked, i go "install complete" i just can't seem to be able to boot into it

&#12540;&#12540;&#12540;
making progress, i get a new boot option in mac os, when pressing the alt key.
i tried another grub install, on sdb.
now i can choose to boot between mac os tiger, windows xp (on the macbook pro's internal hard drive), and on the firewire drive, three systems, two mac OS's (a tiger backup and a leopard), and this new partition recognized as "windows" (firewire)
now this is probably due to the grub install. yet, unfortunately, if i choose the firewire "windows" partition, it end up booting on the internal drive's windows xp partition....

i still haven't been able to boot into the sdb6 xubuntu studio install...








b

---

### Post by dstew on 2009-06-22
If you want to use the Mac OS boot system, I can't help you much because I don't know much about it. If it is a chainloading system, you will need a grub boot loader installed into the boot sector of the Ubuntu partition. To install the boot loader there, you can use an [Ubuntu Live CD]("http://ubuntuforums.org/showthread.php?t=224351"). The problem is, I cannot say for sure what the partition name will be in grub notation. Usually, /dev/sdb6 would be (hd1,5). But the grub shell, which is what you are using on the Live CD, may count the partitions differently than native grub, which is what boots.

If the Mac booter can load and execute a kernel, like grub does, then you   need to set it up for that. I don't know whether the Mac booter chainloads, or boots a kernel like grub. You will have to look on some Mac forums probably to figure that out.

---

### Post by bjaz on 2009-06-22
thanks

i really don't know. a new development

after doing so reading, i found out about rEFIT, and installed that.
i then redid a clean erase reformat (in ext3) mount a / of the ubuntu partition, sdb6, the grub installed on dev/sdb (install works-yet dev/sdb6 doesn't), and sdb2 being my swap,

now when i boot with the firewire drive connected, which has two bootle os's one on which i installed rEFIT, i can choose between the 2 different mac os's, and 2 (don't know why there's two) linux os's, which probably refer to my ubuntu partition, sdb6
entitled linux from HD and linux from EFI

yet neither of them can be booted into. i get 
---------
starting legacy loader using load options "USB"
Error not found returned from legacy loader
the firmware refused to boot from the selected volume. note that external hard drives are not well-supported by Apple's firmware for legacy OS booting
----------

thing is this firewire 800 drive works fine for booting the two mac os's which are on it.
is there anyway to fix this so that i can finally boot into ubuntu ?

thanks

ben

---

### Post by dstew on 2009-06-23
I don't know how your booting system works, but I do know that if you want to chainload grub, you need to install the grub boot loader into the boot sector of the Ubuntu partition, not the MBR of the disk. If the Ubuntu partition is /dev/sdb6, then that is where grub needs to go. You could try to install the grub boot loader there using [the Live CD]("http://ubuntuforums.org/showthread.php?t=224351"), or Supergrub disk. My guess is that the grub shell commands would be```
root (hd1,5)
setup (hd1,5)
quit
```There is no guarantee that the grub shell will properly enumerate the Ubuntu parititon, since it is running a Linux system, and when grub runs during boot time, it is running "natively", and may count the partitions differently than Linux.

---

### Post by bjaz on 2009-06-24
thanks for your help.
i managed to get things working, using rEFit and a grub2 specially designed for external disk booting, with an apple specific setup
			 			[help installing ubuntu with multiple boot options on a firewire 800 drive (macbookpro]("http://ubuntuforums.org/showthread.php?t=1193221")

the ubuntu is now bootable.

i'm starting to wonder if this could allow a similar booting of windows on a firewire drive as well, but this is another story

thanks again

---

