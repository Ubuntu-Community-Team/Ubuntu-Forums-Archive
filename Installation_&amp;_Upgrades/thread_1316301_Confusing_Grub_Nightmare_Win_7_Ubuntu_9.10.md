---
title: "Confusing Grub Nightmare Win 7 Ubuntu 9.10"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by AmbientOcclusion on 2009-11-05
Hi.

I have installed Ubuntu 9.10 after installing Windows 7.

I have OSX installed on sda1 with an efi bootloader. It doesn't work and I have to boot OSX from a usb drive. I nstalled Grub ( /boot) to this partition. It identifies windows and osx but can load neither of them.

On sdb I have both Windows 7 and ubuntu 9.10 ( / )installed. Windows has it's bootloader and the main windows partition. I tried putting grub on this partition and then switching it in bios to boot from this drive first. No matter what I do, with grub on sdb, it just boots the windows bootloader.

Here are the results of **sudo fdisk -l **:
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  GPT
/dev/sda3   *           1           1           0    0  Empty
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b2ab550

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       73412   589578240    7  HPFS/NTFS
/dev/sdb3           73413      108853   284679832+   7  HPFS/NTFS
/dev/sdb4          108854      121601   102398310    5  Extended
/dev/sdb5          108854      109766     7333609+  82  Linux swap / Solaris
/dev/sdb6          109767      121601    95064606   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x225a2221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15298   122881153+   5  Extended
/dev/sdc2           15299       60801   365502847+   7  HPFS/NTFS
/dev/sdc5               1       15298   122881122   83  Linux

Disk /dev/sdd: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13901390

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd2            3188       36481   267434055    5  Extended
/dev/sdd5            3188       36481   267434023+  83  Linux


Here is a screenshot of the partitions:
[img]http://img39.imageshack.us/img39/9925/screenshotpalimpsestdisb.png[/img]

1 Is an EFI Bootloader that never worked. I still must boot OSX with a usb drive.

2 Is the OSX Snow Leopard Drive

3 Is GRUB

4 Is the Windows 7 Bootloader

5 Is The Widnows 7 partition

6 Just an NTFS Storage Drive

7 Swap

8 Ubuntu 9.10 Main Partition

9 Ubuntu 9.10 Home

10 Just an NTFS Parition

11 Old ext4 Jaunty backup home (not really being used)


I don't care about the OSX install not working in grub. I don't mind using a usb drive to boot into it because I only use it for Final Cut. I would like to be able to boot into windows.

Also, if I point the bios to sdb, it tries to boot windows but says the bootloader is messed up and to put in the windows 7 disk to do a repair.

Before I had nearly the same setup with Xp64 where 7 is, Ubuntu 9.04 where 9.10 is and OSX. I just had the bootloader on sdb and it worked fine. If I put the bootloader on sdb the Windows bootloader tries to boot.

Please help! I am not sure what to do.

Thanks ahead of time...

---

### Post by AmbientOcclusion on 2009-11-05
I forgot to add what happens when I select either OS.

With Windows 7 I get no such device error followed by a number.

With OSX I get kernel panic.

---

### Post by AmbientOcclusion on 2009-11-05
Does this mean I will have to re-install an os?

Should I install an older ubuntu?

Not sure what to do here...

---

### Post by AmbientOcclusion on 2009-11-06
Would folks recommend that I install legacy grub? Would this help the problem?

---

### Post by AmbientOcclusion on 2009-11-06
Is there another boot loader loader I can use?

---

### Post by AmbientOcclusion on 2009-11-06
So at this point even theoretical help would be great.

---

### Post by AmbientOcclusion on 2009-11-08
bump

---

### Post by AmbientOcclusion on 2009-11-08
Any ideas?

---

### Post by oldfred on 2009-11-08
I have only read some info on GPT and I understand not many boot loaders recongize GPT. MBR is the old standard since IBM PC's started. Old grub has in some versions modifications to not destroy GPT and new grub2 supposedlly recognizes GPT. While GPT is a Apple standard, it is used for some Windows servers and will be required for drives over 2GB as that is the max for MBR.

I would stay with grub2, if you can in your BIOS set the MBR drive to boot first.
This site has info on reinstalling:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by oldfred on 2009-11-08
Also if you want to know what is booting from where run this script:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text

---

### Post by AmbientOcclusion on 2009-11-14
Hey thanks for those suggestions. I will give them a try and update this list...

---

