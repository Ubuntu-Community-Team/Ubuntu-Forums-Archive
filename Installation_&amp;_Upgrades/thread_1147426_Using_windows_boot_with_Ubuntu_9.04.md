---
title: "Using windows boot with Ubuntu 9.04?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by jamesegreen on 2009-05-03
[FONT=Arial][SIZE=3]I’m new and have an installation problem I need help to resolve.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I have 3 disk drives, a 320GB WD SATA2 with 2 partitions (SATA controller #1) with WinXP installed on the 1st partition, a 250 GB WD SATA2 with 2 partitions (SATA controller #2) with Win2000 on the 1st partition, and a 500GB Seagate SATA2 with 4 partitions (SATA controller #3) on which I am trying to get Ubuntu 9.04 running.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I must have the 2 Windows systems working because all my customers use Windows so I must develop software that runs under Windows (with Visual Studio 2005). 15 years ago I ran Sun Solaris Unix, but switched to Windows because I can’t stand command line only Oss. But now that Ubuntu has what appears to be a nice window GUI, and M$ seems to going down the bloatware road with Vista and Win7, I would like to see if Ubuntu 9.04 can replace M$ Windows.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Note above that I have my XP system on my SATA controller #1 and my Win2K system on my SATA controller #2. I have it that way because I must disable in the BIOS the SATA controllers #3 and #4 to boot into Win2K because it doesn’t handle disks as large as 500 GB. But that happens very rarely, only when I need to run some old software only installed on Win2K.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]But I want to use the Windows boot loader, and call GRUB only when I want to boot Ubuntu 9.04. I have the boot.ini file set up to boot both Win versions correctly. Follows is my sad progression.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]First, I unplugged both Win disk drives, leaving only the 500GB Seagate, and used the Ubuntu 9.04 install disk to format it with a 30GB ext2 partition for Linux (1st partition), a 3 GB linux-swap partition, and a 50GB fat32 partition, leaving one ntfs partition. I then installed Ubuntu with no problem. It installed and rebooted and ran fine.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Then I reconnected my 2 Win disk drives. Formerly, the drives appeared in the order of the SATA controllers on the motherboard, XP, Win2K, the 500GB data disk. After installing Ubuntu, the 500GB data disk now with Ubuntu was the first drive?? Also, I had to use the WinXP SP2 recovery console CD to fixmbr and fixboot to get the windows boot manager back.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I then went through the steps on this forum to reinstall GRUB into the Ubuntu partition and copy its first 512 bytes into a ubuntu.bin file to move to disk C:\ and added C:\ubuntu.bin=”Ubuntu linux” to boot.ini. But when I brought up the win boot loader and selected “Ubuntu linux” I got a blank screen with a blinking cursor.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I then tried several additional loads of Ubuntu with all drives connected. The last time, I deleted all partitions on the Ubuntu drive, created a 30GB ext3 (first) partition, a 3GB linux-swap partition and 2 ntfs partitions (I read that Ubuntu 9 handles ntfs OK). The install went OK, I used the Linux System Rescue CD again to install GRUB to the Ubuntu partition, made a 512 byte ubuntu.bin file, moved it to C:\ and tried to boot Ubuntu. Now I just get the blinking cursor at the top and nothing else happens, but I also went through trials where I got “GRUB” and then nothing, or a dozen GRUBs and then nothing.[/SIZE][/FONT]
 
[SIZE=3][FONT=Arial]I suspect that there is something new in Ubuntu 9.04 that is making the procedure to create the “ubuntu.bin” boot file for C:\ not work properly. This file is supposed to have the GRUB part 1 boot code pointing to the part 2 on the Ubuntu ext3 partition? [/FONT][/SIZE]
 
[FONT=Arial][SIZE=3]Also, I’m confused about the mapping between sd0, sd1 and sd2 and the /dev/sda, /dev/sdb and /dev/sdc symbols, and the disks connected to SATA1, SATA2 and SATA3 hardware controllers.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Any suggestions would be appreciated.[/SIZE][/FONT]

---

