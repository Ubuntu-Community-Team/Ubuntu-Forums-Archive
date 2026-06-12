---
title: "Reinstalled Windows - how to get boot menu back?"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by Thrasonic on 2009-09-05
Hello everyone.  So here's the deal.  I reinstalled Windows a couple of weeks ago and of course I lost my dual boot setup.  I don't know how to get the boot menu back.

I've attached a document showing what my disks look like in Disk Management in Computer Management.  Disk 0 is Windows and Disk 1 has 3 partitions.  The first one at 56 GB is for Linux and is the boot partition.  The second is the swap partition at 4.75 GB.  The third is for data and it's a 405 GB partition.

How can I get the grub boot menu back so I can get into both OS's?

---

### Post by Whiffle on 2009-09-05
Find yourself a copy of the Ubuntu Alternate install CD, boot off it, select the "Rescue Broken System" option, go through the menus, and then sooner or later there will be an option for reinstalling Grub.  Select that, and tell it to put grub on the MBR of whatever your boot device is (usually /dev/sda ).  It should detect your Windows install and add it to grub as well, if it doesn't we can add it to the menu.lst.

---

### Post by Thrasonic on 2009-09-05
Wow that was a quick response.  I don't think the post had been out there for more than five minutes.  I still have a copy of the alternate install CD so I'll give that a try and get back to you.

---

### Post by Thrasonic on 2009-09-05
Okay, I'm at the screen right now in the rescue broken system setup that's asking me which device I want to use as my root file system.  I've given the following choices:

/dev/sda1
/dev/sdb1
/dev/sdb2
/dev/sdb3

I think I'm supposed to use sdb1.  I'm basing this on the fact that there are 3 partitions on one of the hard drives and I'm assuming sdb1, 2 and 3 are all partitions on the same physical hard drive.  Does that sound right to you all?  I'm guessing sda1 represents one single hard drive and that would be my Windows drive.

---

### Post by Whiffle on 2009-09-05
On my system I use the MBR of the main drive that the BIOS looks for at boot, which is usually sda.  The number at the end refers to a particular partition, which I don't think is what you want.  

Hit ctrl+alt+f2, press enter to get a prompt, then run "fdisk -l".  This will show you what the layout of your drives looks like to linux, and help you figure out which partition/drive is what.  Then you can hit ctrl+alt+f1 to get back to where you were.

---

### Post by the8thstar on 2009-09-05
from the live CD, run the following commands

> sudo grub

then

> find /boot/grub/stage1

then, according to which hard disk and partition where Grub is stored, type:

> root (hd?,?)

and 

> setup (hd?)

That should take care of setting Grub to start automatically upon your next reboot.

---

### Post by twright on 2009-09-05
> **Thrasonic said:**
> 
I think I'm supposed to use sdb1.  I'm basing this on the fact that there are 3 partitions on one of the hard drives and I'm assuming sdb1, 2 and 3 are all partitions on the same physical hard drive.  Does that sound right to you all?  I'm guessing sda1 represents one single hard drive and that would be my Windows drive.
You should use which ever one Ubuntu is installed on. The easiest one to find this, as said, is looking at them. It will be the one shown in fdisk -l as ext. The alternative cd is probably easier to do it on than the livecd in any case.

---

### Post by Thrasonic on 2009-09-05
Here's what doing that shows:

Disk /dev/sda: 80.0 GB, blah blah blah
more blah blah blah
more blah blah blah
Disk identifier: blah

Device    Boot  Start  End     Blocks   ID  System
/dev/sda1  *      1    9728    blah      7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, blah blah blah
more blah blah blah
more blah blah blah
Disk identifier: blah

Device    Boot  Start  End     Blocks   ID  System
/dev/sdb1        1     7295    blah     83  Linux
/dev/sdb2       7296   7915    blah     83  Linux swap/Solaris
/dev/sdb1       7916   60801   blah      7  HPFS/NTFS

---

### Post by Thrasonic on 2009-09-05
bump

---

### Post by Whiffle on 2009-09-05
Which drive does the computer look at when it boots?  Whichever one that is, is the one that grub should go on.

---

### Post by Thrasonic on 2009-09-05
I went into the BIOS and found that the hard drives are listed in the following order:

1) 80 GB Windows drive
2) 500 GB Maxtor drive

This is found in Boot menu, Hard Disk Drives.  I can use the + and - keys to change which drive is listed first so I'm pretty certain this means that means GRUB needs to go on the Windows drive.

Sound right?

---

### Post by Whiffle on 2009-09-05
Yep

---

### Post by Thrasonic on 2009-09-05
Okay, I chose sda1 and I got an error message.  It was a big red screen that said:

Mount failed
An error occurred while mounting the device you entered for your root file system (/dev/sda1) on /target.

Please check the syslog for more information.

<Go Back>            <Continue>

I tried Continue but it just takes me back to the previous screen where it asks me to choose which device i want to use as my root file system.

Any thoughts?

---

### Post by Whiffle on 2009-09-05
try /dev/sda   sda1 points to the first partition on sda, we want the MBR of the whole drive

---

### Post by Thrasonic on 2009-09-05
Hmmm... I'm not sure how to do that since I'm not given that option.  The only options I'm given are:

/dev/sda1
/dev/sdb1
/dev/sdb2
/dev/sdb3

I'm doing this using the alternative install CD.  I know that Linux is installed on sdb1.  sdb2 is the swap space and sdb3 is ntfs data storage.  Any other thoughts?

---

### Post by presence1960 on 2009-09-05
you should always have a Live CD even when you install from the alternate. I would download the iso for your installed version and make a Live CD.  Do this: 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by briantoumbs on 2009-09-06
Make a copy of SuperGrub disk on a cd or floppy, it is a great idea to keep it close to you, such a great program.

---

### Post by twright on 2009-09-06
> **Whiffle said:**
> try /dev/sda   sda1 points to the first partition on sda, we want the MBR of the whole drive
No we don't - you should specify the partition on which ubuntu is installed **not just the drive** of the mbr

That would be /dev/sdb1 in this case. :D

---

### Post by Thrasonic on 2009-09-07
> **twright said:**
> No we don't - you should specify the partition on which ubuntu is installed **not just the drive** of the mbr

That would be /dev/sdb1 in this case. :D

Okay, so specify the partition where Ubuntu is installed.  Got it.  I'll give that a shot and let you know what happens.

---

### Post by Thrasonic on 2009-09-07
Okay, so that worked and it let me continue.  Now I'm at a page where it's asking me where I want to install GRUB.  When I first installed Linux I already had Windows on a separate hard drive.  I can't remember it asking me where I wanted to install GRUB - it just asked me if I wanted to install it, period.  At least that's what I remember.  I'm not sure where to install it.  Do I install it to teh MBR of the first hard drive, the Windows drive, or somewhere else?

---

### Post by briantoumbs on 2009-09-07
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

Downloads are on the right side however you want to bur it.
Boot from what ever way you downloaded.

Should look like this when loads.. 

Super Grub Disk ( With Help) =)))))
English Super Grub Disk
Continue till it asks for GNU/Linux or Windows etc
Choose GNU Linux
continue
Fix boot of GNU/Linux

Should goto a black screen and say its been fixed. then you can reboot.

---

### Post by presence1960 on 2009-09-07
> **twright said:**
> No we don't - you should specify the partition on which ubuntu is installed **not just the drive** of the mbr

That would be /dev/sdb1 in this case. :D

Yes you do! If you want GRUB to come up when you boot it must be placed on MBR of the disk, not the first sector of the Ubuntu partition.

You guys/gals are going round & round here. Why doesn't the OP just run the Boot Info Script as requested so we can see exactly what the setup & boot process looks like. This way we can see exactly what needs to be done instead of guessing.

---

### Post by presence1960 on 2009-09-07
> **Thrasonic said:**
> Okay, so that worked and it let me continue.  Now I'm at a page where it's asking me where I want to install GRUB.  When I first installed Linux I already had Windows on a separate hard drive.  I can't remember it asking me where I wanted to install GRUB - it just asked me if I wanted to install it, period.  At least that's what I remember.  I'm not sure where to install it.  Do I install it to teh MBR of the first hard drive, the Windows drive, or somewhere else?

If you want GRUB to come up when you boot it has to be on MBR of the first disk in your hard disk boot order in BIOS. If you want to put it on MBR of another disk then after you install GRUB you must go into BIOS and make that disk first in hard disk boot order so GRUB will take over when you boot.

If you have windows & Ubuntu on separate disks I usually put GRUB on MBR of the disk that has Ubuntu installed on it. Then make that disk first in BIOS hard disk boot order. This will preserve your windows bootloader on the MBR of the disk that has windows on it. You can then boot into Ubuntu and edit/add an entry in your menu.lst for windows.

---

### Post by presence1960 on 2009-09-07
For future reference see the screenshot for how to choose where GRUB gets installed during Ubuntu installation. Default is (hd0) or /dev/sda. That will put GRUB on MBR of sda. if you click the advanced tab you will be presented with options of where you can install GRUB as such:

/dev/sda = MBR of sda
/dev/sda1 = first sector of sda1 partition
/dev/sda2 = first sector of sda2 partition
/dev/sdb = MBR of sdb
/dev/sdb1 = first sector of sdb1 partition
/dev/sdb2 = first sector of sdb2 partition

If you want GRUB to take over at boot it **MUST be on MBR of the first hard disk to boot in BIOS**.

Installing GRUB to  the first sector of a partition is useful when chainloading an installation from an existing GRUB on MBR

---

### Post by Thrasonic on 2009-09-07
Everything is working properly now.  I switched the hard disk order in the BIOS, told the install to put GRUB on the MBR of the first disk, then rebooted and went back into the BIOS and switched the hard disk order back, then rebooted and I was given the GRUB boot loader.  I was able to boot into Windows and Kubuntu from the menu.

Thanks everyone for all of your help.  I really appreciate it.

---

### Post by presence1960 on 2009-09-07
> **Thrasonic said:**
> Here's what doing that shows:

Disk /dev/sda: 80.0 GB, blah blah blah
more blah blah blah
more blah blah blah
Disk identifier: blah

Device    Boot  Start  End     Blocks   ID  System
/dev/sda1  *      1    9728    blah      7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, blah blah blah
more blah blah blah
more blah blah blah
Disk identifier: blah

Device    Boot  Start  End     Blocks   ID  System
/dev/sdb1        1     7295    blah     83  Linux
/dev/sdb2       7296   7915    blah     83  Linux swap/Solaris
/dev/sdb1       7916   60801   blah      7  HPFS/NTFS

looking at this, even with the missing info where you put blah, blah, blah (next time copy/paste the info from output of commands so we can see all of it)
your ubuntu root partition is sdb1. so you want to install GRUB to sdb **not sdb1** then put sdb as first boot in hard disk boot order in BIOS so GRUB will take over when you boot.

P.S. I suggest you run the boot info script as I suggested on page 2 of this thread. This way we can get a clear picture of your setup & boot process. This will show us exactly what needs to be done. Are you tired of going in circles here yet?

P.S. I see you solved it as I was typing this. Enjoy Ubuntu.

---

