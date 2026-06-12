---
title: "Can't use internal hard drive"
date: 2012-10-14
forum: Hardware
---

### Post by inferno92 on 2012-10-14
I used a usb drive to install ubuntu with windows and had several problems installing it. I broken windows somehow then just installed ubuntu over windows but now i can't find/use my internal hard drive plus ubuntu won't boot without my usb drive. Is there anyway i can get ubuntu onto the internal hard drive and also find/use it?

Laptop:HP Pavilion g6
CPU:AMD a6 quad

---

### Post by Bashing-om on 2012-10-14
inferno92; Hi ! Welcome to the forum.

Booting I expect to be a grub(GRand Uinified Bootloader) install situation. In that I expect that grub is installed presently on the usb drive, To boot from the hard drive need grub to be installed onto the hard drive.

Let us see what you have configured on your system.
boot the install cd ->try ubuntu;
command line terminal -> ctl+alt+t
from the command line terminal, post the out put of these commands:
```
sudo fdisk -lu
sudo parted -l
```<lower case "L"s> 

Directions to install grub depends on the out put of the above commands. One-step-at-a-time //huh ?
[INDENT]warm regards <==BDQ

[/INDENT]

---

### Post by inferno92 on 2012-10-14
This is what i got (ima total noob so bare with me)  ....

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   969476095   484737024   83  Linux
/dev/sda2       969478142   976771071     3646465    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       969478144   976771071     3646464   82  Linux swap / Solaris
william@william-HP-Pavilion-g6-Notebook-PC:~$ sudo parted -l
Model: ATA ST500LM012 HN-M5 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4
 2      496GB   500GB  3734MB  extended
 5      496GB   500GB  3734MB  logical   linux-swap(v1)

---

### Post by Bashing-om on 2012-10-14
inferno92; 

Being new to a operating system is nothing to be backward about; We were all innocent at one time !
well, as we knew grub not installed on the hard drive, but the supplied output from the "fdisk" command is not complete. Please submit it again with the header information.
[copy/paste within the code tag (#)at the top of the thread]. I am concerned that the partitioning is GPT ..... if so will have to make provisions for a small boot partition at the start of the drive, to install grub to.

And as a side note, do you intend to have windows again on your system ?
[INDENT]try'n to help <==BDQ
[/INDENT]

---

### Post by inferno92 on 2012-10-15
Don't plan on installing windows on this computer as long as we can get ubuntu working properly. Also you're very helpful :)
Now how to i go about getting grub installed properly? If you have link, vid, or team viewer like program you can give me it would help bunches

---

### Post by NikTh on 2012-10-15
Hi , 

try to correct the grub-bootloader via this tool : [Boot-repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

Windows does not exist in your system anymore. The output of helpful commands that [Bashing-om]("http://ubuntuforums.org/member.php?u=1111508") suggested pointed that. 

Good luck. 
Thanks

---

### Post by Bashing-om on 2012-10-15
I am pleased to assist you, as windows is no longer a consideration, and we are not dealing with huge disk; It is my suggestion that you re-format to msdos (that is ubuntu's MBR) this necessitates a re-install, good thing is that this will take care of the partition mis-alighnment.

So. from the live/install cd ->try ubuntu
click dash -top button on the launcher- (left side of screen) ->search box
enter into it the term GParted -> below the Gparted icon appears
in Gparted select device -> new ->choose to format to msdos (yeah we are going to wipe the disk entirely and install a new partition table).
exit out of Gparted

back on the desktop -> install ubuntu
choose to use the entire disk option
check the boxes for install updates during install and for 3rd party software
look for the oblong box at the bottom of one of the install screens for where the installer will install grub. You want grub installed to sda// Otherwise again grub will be installed to the usb device.

The wizardly install will do you nicely for now. When you are comfortable with ubuntu you may desire particular partitioning to suit your needs at THAT time.

It is late in my time zone and I am tired, calling it a night, will check on you in my AM.[INDENT]Welcome to the wonderful world of open source where there are no secrets!   
[/INDENT]

---

### Post by inferno92 on 2012-10-15
I'll need to make another boot-able drive and will wipe and reinstall everything later on. I broke everything i guess XD

---

### Post by Bashing-om on 2012-10-15
Ok, ...The only thing you have done wrong is not do some homework before starting this operation.
some background info: Windows is greedy and does not play nice with ubuntu, ubuntu plays nice with everyone ! The older disk arrangements only permitted 4 primary partitions per disk, and windows generally used all  of them. Requiring some shuffling around to get a partition to install ubuntu onto (possibly the original slopyation).

 Additionally the disk was formated GPT which ubuntu can deal with, sometimes requiring prior preparation. As I said above, windows no longer a consideration and no huge disk, and with the partition alignment not perfect -> reformat the disk -> enabling a simpler boot process that is easier to maintain.

The install process: Does your system have a cd drive ? Personal use habits on my part I prefer to have the install on a cheap cd. Thus I have a "live" cd handy for troubleshooting/investigation purposes, as well as easy to transport to other systems.
The install cd has GParted installed, be aware can not operate on a 'mounted" partition, so, you really do need the install medium with GParted -> when booted up from the "live" (installer) cd, then the system partitions are not mounted by default.

 Panic not. Just proceed in a calm and orderly fashion.

and you will be up and running.
[INDENT]regards <==BDQ
 
[/INDENT]

---

### Post by inferno92 on 2012-10-15
Yay \(*o*)/! it works!!! TYVM you guys for all the help :D

---

### Post by Bashing-om on 2012-10-15
Outstanding, you do good work !
Please detail your solution for the next person seeking a solution
and please mark this thread as "solved" from the thread tools options at the top of the post. (aids others in searching)
[INDENT]happy ubuntu'n <==BDQ

[/INDENT]

---

