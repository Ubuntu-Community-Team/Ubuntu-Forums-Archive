---
title: "Mounting XP NTFS HD..."
date: 2009-07-27
forum: Hardware
---

### Post by LatinHacker on 2009-07-27
> 
I reinstall Windows XP, after that I had to rescue the GRUB because Windows would not allow me to boot into Linux Ubuntu; but now I cannot load windows.  When I was repairing the GRUB, I set **sda1** as **/windows**. the bootloader says it is on **(hd0,0)** and when I try mounting the NTFS partition which is like this:

```

root@latinhacker-14:~# fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2566    20611363+   7  HPFS/NTFS
/dev/sda2            2567        4863    18450652+   5  Extended
/dev/sda5            2567        4845    18306036   83  Linux
/dev/sda6            4846        4863      144553+  82  Linux swap / Solaris

mkdir /media/LatinHacker
root@latinhacker-14:~# mount /dev/sda1 -t ntfs /media/LatinHacker
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```I also tried:

```

mount /dev/sda1 /media/LatinHacker

mount: you must specify the filesystem type

```What should I do?  :confused:

> **PabloTwo said:**
> I'm not sure if it will make any difference, but try the mount command this way:
```
mount -t ntfs /dev/sda1 /media/LatinHacker
```
...without splitting the /dev/partition and /mountpoint with the -t option.

Apparently the partition **/dev/sda1** got damaged, I think it was because as I was repairing the GRUB, I discovered some anomalies on **/dev/sda1** and on **/dev/sdb1,2** so I ran fdisk, and I verified them, and then re-wrote the content table.

The weird thing is that, my boot flag is on **/dev/sda1** which suggest that it is, at some level, working, I tried changing my boot flag to **/dev/sda5** but the BIOS told me that there was no OS.  So, I had to turned the boot flag back to **/dev/sda1** from the Live CD using GParted.

My next question would be, Is there a way to move my GRUB system to **/dev/sda5**?  So that I can create an image backup of my Linux System and re-installed XP.  and then restored to **/dev/sda5** the whole system as it is now, including the GRUB.

Now, I suspect, that if the boot flag is on **/dev/sda1**, even if from a Live CD I restore the Linux system, I would have to turned from this Live CD the boot flag, back to **/dev/sda5** and that would make everything alright.  Since GRUB is already configured to start XP from **(hd0,0)**.  Am I right?

---

### Post by LatinHacker on 2010-03-08
Nothing worked, I had to reinstall both systems, Windows 1st and then, Linux Ubuntu.](*,)

---

### Post by Herman on 2010-03-31
> When I was repairing the GRUB, I set **sda1** as **/windows**. the bootloader says it is on **(hd0,0)**Hello LatinHacker,
I'm sorry to read of your problems with Windows XP and I'm sorry I'm too late to be of any help.
It appears as if you have installed GRUB to the boot sector of your Windows partition, which is not a good thing to do. 
Everything would have been okay if you had installed to MBR in your first hard disk instead.
> Now, I suspect, that if the boot flag is on **/dev/sda1**, even if from a Live CD I restore the Linux system, I would have to turned from this Live CD the boot flag, back to **/dev/sda5** and that would make everything alright.  Since GRUB is already configured to start XP from **(hd0,0)**.  Am I right?     GRUB doesn't need the boot flag and neither does Linux, the boot flag, if anywhere, should be allowed to remain on your Windows partition, but the position of the boot flag isn't the main problem here at all.

:)  Let me explain a few terms.
The MBR of your first hard disk, (where you should install GRUB, (or rather, code pointing to GRUB), is in the first sector of every hard disk, and in addition GRUB uses some of the sectors after that in the first track of the hard disk, which is normally empty.
Your MBR is designated as /dev/sda in Linux and (hd0) by GRUB.

Your Windows boot sector is the first sector of your Windows partition, commonly located in sector number 63 if you have Windows XP or earlier. Your Windows boot sector needs to contains pointers to the Windows boot loader so you can boot Windows.
Your Windows boot sector is designated as /dev/sda1 by Linux if Windows is in partition number1, which is usually the case.
This is called (hd0,0) by GRUB, and you should never install GRUB to your Windows boot sector, as you found out. 

Ways you could have repaired your Windows installation include, 

[LIST]
[*]running dosfsck from Ubuntu if you have Windows XP or earlier with the FAT32 file system, [When the bootsector is not the same as its backup]("http://members.iinet.net.au/%7Eherman546/p10.html#differences_between_the_bootsector_and_its_backup") - FAT32.
[/LIST]
, or for Windows XP or later with NTFS, 

[LIST]
[*]running FIXBOOT from a Windows XP [Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm")
[*]using a dd command from Ubuntu to replace the Windows NTFS boot sector with its backup
[*]or running TestDisk in Ubuntu or in a Linux LiveCD,  [12 NTFS Boot sector recovery]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery").
[/LIST]
 ... to name a few.

The reason why mistakes like this happen is because there are many so called 'experts' who continue to confuse the terms 'MBR' and 'boot sector' interchangeably, and to make matters even worse, some people refer to a mythical thing they call 'the Windows MBR'.
People new to Linux read these misnomers and naturally they are confused and misled.

To avoid repeating the same mistake in the future you just need to learn the difference between a MBR (the first sector of a hard disk),  and a boot sector, (the first sector of a Windows partition), and how Linux and GRUB partition numberings work. :)

[URL="http://members.iinet.net.au/%7Eherman546/p10.html#Restore_an_NTFS_boot_sector_with_its"]
[/URL]

---

