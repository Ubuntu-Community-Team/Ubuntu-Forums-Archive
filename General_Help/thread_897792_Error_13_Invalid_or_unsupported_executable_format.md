---
title: "Error 13: Invalid or unsupported executable format"
date: 2008-08-22
forum: General Help
---

### Post by haiiyaa on 2008-08-22
Hello, 

I am having a serious problem with my Ubuntu installation. I have Dell XPS M1530. It's a dual boot with Windows Vista and Ubuntu Hardy. Things had been running fine, till a couple of days ago when I started having problems with my wireless connection and some applications didn't load properly. I restarted my computer and then I got Grub Error 17. So, now i wasn't able to log into either windows or linux. Finally, now using Super Grub, if i select to load the windows paritition it loads up fine. But, if I try to load the linux partition, i get the following message. and nothing happens. 

Booting '4 hda4 sda4 (hd0,3) hd0s4 Linux 136 GB '

set out_device=(hd0,3)
set out_hurd_hd=hd0
set out_hd=hd0
set out_linux_letter=a
set out_lide_hd=hda
set out_lscsi_hd=sda
set out_part=(hd0,3)
set out_lide_part=hda4
set out_lscsi_part=sda4
set out_hurd_part=hd0s4
set out_linux_part=a4
set out_part_n=3
set out_linux_end=a4
back
back
set aux_part=(hd0,3)
rootnoverify (hd0,3)
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue
---------

Please help, I am not a linux expert, and I am desperately trying to become a linux fan. As soon as i start liking it and get past the headache of configuration i have a major set back. I have a lot of important information on this partition and I have to retrieve it. 

Thanks

---

### Post by coffeecat on 2008-08-22
Some words of explanation, so you can understand what's gone wrong here. Stage 1 of the grub bootloader is the first 400 bytes or so of the hard disc, on the area called the mbr. Stage 1 loads stage 1.5 which occupies a small space on an otherwise unused part of the HD just after the partition table. Stage 1.5 in turn loads stage 2 which is in the /boot/grub folder of your Linux root partition (this seems to be sda4 in your case). Stage 2 loads the grub menu (menu.lst - in the same folder as stage 2). From there, grub starts the boot process, either of Windows or in the case of Linux by uncompressing the Linux kernel.

Error messages from the Grub Manual:

> 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.Interpretation: stage 1.5 can't recognise the filesystem on your Linux root partition and therefore cannot initiate grub stage 2.

And with supergrub:

> 13 : Invalid or unsupported executable format
This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD)Something's seriously wrong on your Linux root partition.

Question: did you suffer a hard shutdown before this happened, or anything that might cause a filesystem corruption?

I don't know whether your Linux filesystem is damaged beyond repair, but the first thing to do is to boot up with the live CD, open a terminal and post the output of:

```
sudo fdisk -l
```That's a lower-case L, not one. If you can connect to the interent from the live CD, you can copy and paste from the terminal - that will save a lot of tedious typing. The output of fdisk may be useful before going on to filesystem repair utilities which are on the live CD.

---

### Post by haiiyaa on 2008-08-22
To answer your question about the hard shutdown, yes I did have to do that. I closed my laptop and that for some reason didn't put the computer in suspend mode (normally it does do it). And so my computer battery died. I think the problems started after that. 

Here is the output of fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4f51509

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326    6  FAT16
/dev/sda2   *          12       11534    92558497+   7  HPFS/NTFS
/dev/sda3           11535       12538     8064630   82  Linux swap / Solaris
/dev/sda4           12539       30401   143484547+  83  Linux

Let me know if there is anything else i can provide. 

Thanks

---

### Post by coffeecat on 2008-08-22
The good news is that fdisk recognised a valid ext3 partition at /dev/sda4. This has to be your Ubuntu root partition because sda1 is a Dell recovery partition (I guess), sda2 your Windows C: partition and sda3 your Ubuntu swap partition.

An ext3 partition recognised by fdisk hopefully means a repairable one.

However, I'm in danger of getting out of my depth here, so I'm going to be cautious in what I say next. If this was my computer I would boot up the live CD again and try running fsck on /dev/sda4, but not before doing some googling and searching around. I must admit I have minimal experience of repairing filesystems with fsck - if only because I have been relatively lucky thus far. Anyway, a few pointers for you. You need to read man fsck, which you can do in the live CD, but [this link]("http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm") might be easier to read. That was the first decent link that came up when I googled 'Linux fsck manual' but you might find something more comprehensive.

I have another suggestion but I don't know which is the wiser option. It may be that the damage is entirely/mostly in /boot, which is why grub is failing, and it may be possible to mount sda4 from the live CD and copy your important data off with it. But I don't know whether it would be safer to perform fsck first or to try and copy your data off and then try to repair the filesystem with fsck.

If you do wish to try to copy data off sda4 before trying fsck, you can simply go to Places > Computer and double-click on the icon representing sda4, navigate to your home folder and copy onto a USB drive or wherever you want to copy to. One problem you might have is that the UID (user identity) for the live CD is probably different to your UID in your installed version, in which case you will get a permission denied error. The answer to this is to open a root-owned nautilus (with 'gksudo nautilus') and copy with that onto either a FAT32 formatted drive or NTFS-formatted drive so that you don't get permission problems when you try to access the files on the USB drive.

But you might want to wait for other opinions before deciding whether to copy off or repair with fsck first.

Good luck.

---

### Post by haiiyaa on 2008-08-22
Just out of curiosity, i was trying to see if i can even see the partition in places -> computer. Unfortunately, it is not there. I think the next option I have is the fsck route, unless someone else has a better idea before I read through the fsck manual. 

thanks for your inputs.

---

