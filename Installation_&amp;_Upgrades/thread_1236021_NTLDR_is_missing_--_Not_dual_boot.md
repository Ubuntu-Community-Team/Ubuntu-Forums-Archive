---
title: "NTLDR is missing -- Not dual boot"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by vwi on 2009-08-09
I've installed Ubunto on a Dell with two hard drivers and raid 0. I told the installation to install Ubunto using the entire disk. Now I get an NTLDR is missing message when I boot. All the threads I've found on this subject involve dual boots. I'd don't want to dual boot.
 
I've search through the BIOS setup, but can't see anything relevant to the problem. Help would be much appreciated. Thanks

---

### Post by running_rabbit07 on 2009-08-09
Can you boot the LiveCD? If so can you post the output of 

sudo fdisk -l

You will have to open a Terminal under the Applications>Accessories menu to enter the command.

(that is an L not a 1)

---

### Post by vwi on 2009-08-10
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]To run a command as administrator (user "root"), use "sudo <command>".[/FONT][/SIZE][/FONT]
[FONT=Nimbus Mono L][FONT=Batang][SIZE=3] [/SIZE][/FONT][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]See "man sudo_root" for details.[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][FONT=Batang][SIZE=3] [/SIZE][/FONT][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][FONT=Batang][SIZE=3] [/SIZE][/FONT][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]Disk /dev/sda: 250.0 GB, 250000000000 bytes[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]255 heads, 63 sectors/track, 30394 cylinders[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]Disk identifier: 0x41ab2316[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][FONT=Batang][SIZE=3] [/SIZE][/FONT][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]   [FONT=Nimbus Mono L]Device Boot      Start         End      Blocks   Id  System[/FONT][/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]/dev/sda1   *           1       30020   241135618+  83  Linux[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]/dev/sda2           30021       30394     3004155    5  Extended[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]/dev/sda5           30021       30394     3004123+  82  Linux swap / Solaris[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][FONT=Batang][SIZE=3] [/SIZE][/FONT][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]Disk /dev/sdb: 250.0 GB, 250000000000 bytes[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]255 heads, 63 sectors/track, 30394 cylinders[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]Disk identifier: 0x41ab2316[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][FONT=Batang][SIZE=3] [/SIZE][/FONT][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]   [FONT=Nimbus Mono L]Device Boot      Start         End      Blocks   Id  System[/FONT][/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]/dev/sdb1               1           9       72261   de  Dell Utility[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]/dev/sdb2   *          10       29901   240107490    7  HPFS/NTFS[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]/dev/sdb3           29902       30393     3951990   db  CP/M / CTOS / ...[/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][SIZE=3][FONT=Batang]ubuntu@ubuntu:~$ [/FONT][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Nimbus Mono L][FONT=Batang][SIZE=3] [/SIZE][/FONT][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

---

### Post by merlinus on 2009-08-10
What is the boot order of your hdds in bios?  Acccording to fdisk, windows is installed on sdb2, and linux on sda1.

---

### Post by vwi on 2009-08-10
You nailed the problem. I solved it myself by trial and error. In Setup, I disabled sda2 and enable sda1. Ubuntu booted! Better yet, I found the wireless setup, put in my SSID and password and I'm replying now on my new Linux system. Cool!

thanks everyone for your support.

good night!:)

---

### Post by running_rabbit07 on 2009-08-10
> **vwi said:**
> You nailed the problem. I solved it myself by trial and error. In Setup, I disabled sda2 and enable sda1. Ubuntu booted! Better yet, I found the wireless setup, put in my SSID and password and I'm replying now on my new Linux system. Cool!

thanks everyone for your support.

good night!:)

Sweet! Welcome to Ubuntu!

---

