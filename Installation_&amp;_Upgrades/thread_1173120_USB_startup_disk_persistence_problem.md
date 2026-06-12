---
title: "USB startup disk persistence problem"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by jamesbeat on 2009-05-29
I Hope this is the right place to post this, I'm having a little trouble with USB startup disk creator.

I used an old 4gb flash drive, formatted it to fat16 and flagged it as boot in gparted and used the tool to make a startup disk using all of the extra space on the drive for a persistent version.
Unfortunately, although it works fine as a 'live cd', any changes I make are not stored for some reason.

I made one for a friend using his 2gb flash drive and that works fine, saving his configuration etc. I followed the exact same steps with my drive, the only difference being the actual flash drive I used, and the fact that the capacity is 4gb instead of 2gb

Any ideas?

---

### Post by WildeBeest on 2009-05-29
I have the same problem with a Corsair 4GB USB flash drive.

---

### Post by TroN-0074 on 2010-11-25
Is there a guide on how to create a bootable USB with the persistence mode on? I am planning on doing this myself but I cant find a way to do it with Ubuntu 10.04 LTS.
It will be highly appreciated it.

---

### Post by wilee-nilee on 2010-11-25
> **TroN-0074 said:**
> Is there a guide on how to create a bootable USB with the persistence mode on? I am planning on doing this myself but I cant find a way to do it with Ubuntu 10.04 LTS.
It will be highly appreciated it.

Are you using the startup disc creator in Ubuntu or can you? There are a couple of ways to do it, just identify the operating systems you have to work with. Also how big is the thumb drive?

---

### Post by C.S.Cameron on 2010-11-25
Following for making a persistent drive using -rw partitions:
(You might just want to check your text.cfg file to see if "persistent" is there as shown below).


Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.

---

### Post by TroN-0074 on 2010-11-25
Thank you for these advices.
I am looking to buy a 16 GB flash drive and dedicate the whole thing to ubuntu. But I would like to set it up so it will save the changes and setting from every session. So if I am at school or work I can boot from the USB and get in my personal files. I do have starup disk creator, I already have the ubuntu iso cd file downloaded, and I have disk utility manager up and running. I was just looking for a guide on how to do it.

---

### Post by C.S.Cameron on 2010-11-26
With a 16GB pendrive you might want to consider a Full install:
Step by step method for 10.10 follows:

Turn off and unplug the computer. (See note at bottom)

Remove the side from the case.

Unplug the power cable from the hard drive.

Plug the computer back in.

Insert the flash drive.

Insert the Live CD.

Start the computer, the CD should boot.

Select language

Select install Ubuntu.

Select Download updates while installing and Select Install this third-party software.

Forward

At "Allocate drive space" select "Specify partitions manually (advanced)".

Forward

Confirm Device is correct.
(Optional partition for use on Windows machine)

Select "New Partition Table" click Continue on the drop down.

Click "Free space" and "Add".

Select "Primary".

Make "New partition size..." about 4GB.

Location = Beginning.

"Use as:" = "FAT32 file system"

And "Mount point" = windows.

Select "OK"

Click "free space" and then "Add".

Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)

Click "free space" and then "Add".

Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hybernation)

Click "free space" and then "Add".

Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)

Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".

Select your location.

Forward.

Select Keyboard layout.

Forward.

Insert your name, username, password, computer name and select if you want to log in automatically or require a password.

Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.

Select forward.

Wait until install is complete.

Turn off computer and plug in the HDD.

Stick the side panel back on.



Note:

You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by TroN-0074 on 2010-11-26
Sweet, thanks!

---

