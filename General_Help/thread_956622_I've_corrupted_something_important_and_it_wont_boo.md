---
title: "I've corrupted something important and it wont boot"
date: 2008-10-23
forum: General Help
---

### Post by Handssolow on 2008-10-23
I cant now boot Heron from my IDE hard drive. I was wanting to put 8.10 beta on a pen drive so I was running 8.10 from a live CD. I downloaded and ran u810 from pendrivelinex.com and by mistake I entered the wrong drive letter -my working hard drive. Realising what I'd done I aborted the program but it was too late, my hard drive had been corrupted.

Booting from a live Heron CD my hard drive is shown as ubuntu8 with no files visible. Properties shows 16kb used, 19Gb free (It should be showing 40Gb hard drive all Ubuntu HHeron), and the file system is msdos.

Supergrub gives error 15 and no boot/grub/stage1

Here is the output of sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc3ccc3c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2499    20073186    c  W95 FAT32 (LBA)
/dev/hda2            4792        4998     1662727+   5  Extended
/dev/hda5            4792        4998     1662696   82  Linux swap / Solaris


Being in unknown territory, I'm in urgent need of help.

---

### Post by Handssolow on 2008-10-23
My live Heron CD has no resue option at the start up. If it did would this offered a mechanism to recovery my system and which live CD do I need instead?

Help

---

### Post by Handssolow on 2008-10-23
I'm stumbling in the dark here.
I've booted up my live CD of 7.10 to check for a recovery option, which there wasn't.

Working with sudo grub in the terminal I get

grub> root (hd_
Error 23: Error while parsing number

grub> find /boot/grub/stage1

Error 15: File not found

grub> setup (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> setup (hd0,

what do I do next, can I recovery my 8.01 OS without having to re-install?

I've added the following information. Not sure I like this. Shouldn't there be other partitions?

grub> geometry (hd0)
drive 0x80: C/H/S = 4998/255/63, The number of sectors = 80293248, /dev/hda
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 4,  Filesystem type unknown, partition type 0x82

---

### Post by davidcaiazzo on 2008-10-23
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Handssolow on 2008-10-23
Unfortunately I get stuck with-
grub> find /boot/grub/stage1
Error 15: File not found

Earlier I've tried using rescue mode on the 8.04 alternate install CD.
When I come to the option "execute a shell in /dev/hda1" I get the message-
no usable shell was found on your root file system (/dev/hda1)

Looks like I've turned my Linux boot partition into a windoze one?

Any further ideas?

---

### Post by Crossyboi on 2008-10-23
> **Handssolow said:**
> Unfortunately I get stuck with-
grub> find /boot/grub/stage1
Error 15: File not found

Earlier I've tried using rescue mode on the 8.04 alternate install CD.
When I come to the option "execute a shell in /dev/hda1" I get the message-
no usable shell was found on your root file system (/dev/hda1)

Looks like I've turned my Linux boot partition into a windoze one?

Any further ideas?


It does seem that you have corrupted the partition! my LiveCd has a partition  manager on it (Make sure you boot to CD) where you could delete and recreate the partitions. But you might still find some problems with Grub, just make sure you have the same OS or OSs' installed and you should be fine!

---

### Post by Handssolow on 2008-10-23
I guess you're right Crossyboi, it looks like I'll need a tool to alter the /dev/hda1 partition from W95 Fat32 (LBA) back to Linux.

I would appreciate some advice as to the exact steps that I'll need to take. and the likely success or otherwise.

testdisk looks a promising recover tool, anyone with any experience in this context or can booting from a live alternate HH CD also do the same job?

---

### Post by Crossyboi on 2008-10-24
> **Handssolow said:**
> I guess you're right Crossyboi, it looks like I'll need a tool to alter the /dev/hda1 partition from W95 Fat32 (LBA) back to Linux.

I would appreciate some advice as to the exact steps that I'll need to take. and the likely success or otherwise.

testdisk looks a promising recover tool, anyone with any experience in this context or can booting from a live alternate HH CD also do the same job?

Yeah im pretty sure the HH CD will do the same job, I know you need a Linux-swap file and then a different partition to install Ubuntu back onto, because I don't know what other OS's you might of had, if you just had HH on it then just reinstall it once you have recreated the partitions.

---

### Post by caljohnsmith on 2008-10-24
You can use fdisk to change your hda1 partition back to linux:
```
sudo fdisk /dev/hda
```
Then choose "t", then "1" for the partition number, then type "83", then "w" to write the change. Then see if it is possible to mount it:
```
sudo mount /dev/hda1 /mnt
```
If that doesn't work, try:
```
sudo fsck -y /dev/hda1
```
And if that says it completed successfully, try and mount hda1 again. Let me know how it goes. :)

---

### Post by Handssolow on 2008-10-26
Unfortunately my error with the pen drive software both created a new boot partition and shrank my Linux boot partition. After several hours yesterday with testdisk and gparted I managed to expand the Linux boot partition so removing the unwanted W95 FAT partition, after I used dd rescue, several of my old files had re-appeared. Looking back perhaps I might have been able to copy some old files to a memory stick, anyway another tweak with gparted and things were worse. I'd had enough.

I have a partial backup available from last year but although I've not lost anything really important, I'd rather it not happened. I'll be making more frequent back ups in future!!!

A fresh install of Heron 8.04 did not bring an eth(0) connection so after an hour I installed 8.10 Beta Intrepid which connected almost immediately. I'm wondering if Firefox is working 100% OK otherwise the OS seems fine.

On a brighter note. my desktop PC now has a new kernel with Intrepid and doesn't need any acpi modification to the kernel line in menu.lst to get it to boot and it powers down normally, something it's not done for 9 months.

---

