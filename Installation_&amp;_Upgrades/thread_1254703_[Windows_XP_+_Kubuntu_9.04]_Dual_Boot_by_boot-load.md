---
title: "[Windows XP + Kubuntu 9.04] Dual Boot by boot-loader of Windows XP: GRUB Error 18 !"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by rafaelcarvalho on 2009-08-31
I have a problem that I am not able to deal at all and is chasing me almost a week. 
 
**_THE PROBLEM_**: Take a dual boot with Windows XP and Kubuntu 9.04 by the boot loader of Windows XP in MBR (and not the GRUB!), with the Windows menu the first menu to appear when turning on the computer! 
 
_Equipment_: Laptop Compaq Presario V6210BR with 30 GB HD.
 
_Partitions_:
 
[FONT=Courier New]Disk /dev/sda: 60.0 GB, 60022480896 bytes[/FONT]
[FONT=Courier New]255 heads, 63 sectors/track, 7297 cylinders[/FONT]
[FONT=Courier New]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
[FONT=Courier New]Disk identifier: 0x100f59dc[/FONT]
 
[FONT=Courier New]Device Boot Start End Blocks Id System[/FONT]
[FONT=Courier New]/dev/sda1 * 1 3647 29294496 7 HPFS/NTFS **(Primary)**[/FONT]
[FONT=Courier New]/dev/sda2 3648 7297 29318625 5 Extended[/FONT]
[FONT=Courier New]/dev/sda5 3648 4255 4883728+ 83 Linux **(Logical)**[/FONT]
[FONT=Courier New]/dev/sda6 4256 4379 995998+ 82 Linux swap / Solaris **(Logical)**[/FONT]
[FONT=Courier New]/dev/sda7 4380 4865 3903763+ 83 Linux **(Logical)**[/FONT]
[FONT=Courier New]/dev/sda8 4866 7297 19535008+ b W95 FAT32 **(Logical)**[/FONT]
[FONT=Courier New]usuario@usuario-laptop:/$[/FONT]
 
Windows is installed on partition 1 ( primary, C: ) and the root of Kubuntu on sda5. 
 
With GRUB installed on MBR, the boot is occurs perfectly with NO PROBLEM! He gives the boot both Kubuntu and Windows normally:
 
_GRUB_:
- Ubuntu 9.04, kernel 2.6.28-11-generic
- Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
- Ubuntu 9.04, memtest86+
- Windows XP
 
I repeated the tip found the hills on the Net:
 
Image of the boot sector of Kubuntu:
**sudo dd if=/dev/sda5 of=bootsect.lnx bs=512 count=1**
 
Copy to C:\ Windows and then change the boot.ini: 
**c:\bootsect.lnx="Linux"**
 
As a test, if the GRUB to the MBR I choose the "Windows XP" and goes to the next screen is the Windows boot loader, and the option "Linux" to appear in the boot loader menu of Windows XP, but when I select gives a infamous "error 18":
 
_MENU BOOT LOADER WINDOWS XP_:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\bootsect.lnx="Linux"
 
_ERROR IN CHOOSING "Linux"_:
 
**Loading stage2**
 
**GRUB loading, please wait...**
**Error 18**
 
 
Look, I'm a few days ago I tried everything and nothing! I looked on "GRUB Error 18" and found something about configuration specific HD in the bios setup, but my computer does not have any option for configure anything, just following the order of the boot. 
 
I followed suggestions not to install Kubuntu at the end of HD that could have problems being encountered by GRUB and nothing! 
 
Installing Linux on the primary partition and nothing!
 
I also tried to install Kubuntu (or a "/boot" partition) on the first partition on the HD, at the very beginning, AND NOTHING! 
 
I'm Starting to get stressed out ... 
 
And the funny thing is that when GRUB is "in command" of the boot everything works fine, the problem is just getting Windows to starts Kubuntu by the boot loader! And if I give a "fixmbr" the Recovery Console XP and leave only the Boot Loader in the MBR, also can not boot in Kubuntu! 
 
Please, I need help! 
 
I thank you! 
 
Att; 
 
 
Rafael

---

### Post by stlsaint on 2009-08-31
curious...not to seem like a mean guy or anything but if you say Grub works perfectly...?? see where im going with this? whats the motive to change?

---

### Post by rafaelcarvalho on 2009-08-31
Stlsaint,
 
Thanks for the answer.
 
I was hired to do this service and the customer demanded that Windows was in "control" of the boot. 

Do what you know ...
 
It is hard to put the ubuntu in window's bootloader!

---

### Post by rafaelcarvalho on 2009-08-31
I noticed one thing: When the GRUB boot gives, and that all work right, it show message "**Loading stage1.5**" ... 

And in the windows bootloader, when I select the "Linux" and gives the "Error 18", it show message "**Loading stage2**" ... 

Does problem is here? The "stage2" ???

---

### Post by presence1960 on 2009-08-31
I hate to say this because I am not a fan of using Windows especially to boot Linux (it is sacrilidge to me) & I am not a fan of Easy BCD, but you should install Easy BCD to boot Linux from Windows.

oops, forgot the link: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by rafaelcarvalho on 2009-08-31
Hi presence1960, thanks for help!

I downloaded the program, but is for use with Vista only.

I tried one new type of partitioning, with a small partition "*/boot*" in the begin of HD, but in try load the image of "sda1" in XP's bootloader the **error 18** remains...

[FONT="Courier New"]Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x100f59dc

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  83  Linux **(/boot)**
/dev/sda2   *           7        3653    29294527+   7  HPFS/NTFS **(Windows)**
/dev/sda3            3654        7297    29270430    5  Extended
/dev/sda5            3654        4261     4883728+  83  Linux **(/)**
/dev/sda6            4262        4747     3903763+  83  Linux **(/home)**
/dev/sda7            4748        4871      995998+  82  Linux swap / Solaris **(swap)**
/dev/sda8            4872        7297    19486813+   b  W95 FAT32
linustorvalds@linustorvalds-laptop:/$[/FONT]


IT'S HARD !!!

---

### Post by rafaelcarvalho on 2009-09-01
**DID IT!! PROBLEM IS OVER!**

I left the first partition as "/ boot" and made the image of "sda" instead of "sda1"... 

Copied for C, edited the boot.ini...

Then I give a FIXMBR in the Recovery Console on Windows.

Now the XP's bootloader is the first boot menu and when I choose the "Linux" option, that go to GRUB's start menu (as I wanted) and in the GRUB menu just choose a kernel option to boot normally it gives!

---

