---
title: "512 GB flash thumb drive"
date: 2012-06-22
forum: Hardware
---

### Post by d.w on 2012-06-22
Running 12.04 by itself on clean hard drive on  HP AMD quad core 7 gb
laptop using Gnome 3 desktop.    The flash drives in question are Rohs
CE FCC 512 gb USB 2.0 and are brand new. The drives work on Windows and
my other usb thumbs work fine on 12.04 on this computer.  Either 5121gb
drive is visible using Disk utility from the desktop, and it shows up on
lsusb.

cowboy@U02B:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB

Bus 001 Device 075: ID 0591:1624 Questra Consulting   (This is the Drive
in question)

Bus 003 Device 002: ID 5986:02ac Acer, Inc 
Bus 005 Device 002: ID 138a:0018 Validity Sensors, Inc. 
Bus 004 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical
Wheel Mouse
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 007: ID 04d9:1702 Holtek Semiconductor, Inc. 

This drive does not show up in the desktop menus.  With the drive
inserted Gparted will hang in search.  I think that a linux tweak is
needed as fedora 17 and knoppix live disks show the same results or
symptoms.  

I do not need plug and play.  Terminal access is fine if someone can
please walk me through it.    I have two of these 512 gb thumb drives
and I do not want to go back to Windows.  If linux will not run flash
512gb, how many gigs will linux handle?  Clue me in if you can folks.
Thanks for reading this and I trust some nice person will solve this.

---

### Post by ahallubuntu on 2012-06-22
Could you mean 512MB?  I can't find 512GB drives for sale anywhere; if so, they must be very new and very expensive.  NewEgg sells only one 256GB USB flash drive, and it sells for $836.63 USD.

Any chance the drives are encrypted with some software on the drive?

What is the exact make/model of the thumb drives?

In a terminal, try typing

sudo fdisk -l /dev/sdb

assuming the drive shows up as sdb and your single hard drive is sda.

---

### Post by d.w on 2012-06-22
The thumb drives are Rohs CE FCC 512 gigabyte and are very ordinary not encrypted or mil-spec, what you will see  at best buy soon,  China electronics with the typical total lack of documentation. They are window xp and Mac OS, usb 2.0 and 1.1 compatible. The price of flash drives is going to CRASH.  I was in the right place at the right time and could afford the expenditure which was quite reasonable.  So reasonable that if Linux can't run these drives then I will have yucky windows in my pocket which can run them.

Here's the terminal result.    

cowboy@U02B:~$ sudo fdisk -l /dev/sdb
[sudo] password for cowboy: 

Disk /dev/sdb: 536.9 GB, 536870912000 bytes
214 heads, 31 sectors/track, 158060 cylinders, total 1048576000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x153cd85e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2920  1048575999   524286540    b  W95 FAT32
cowboy@U02B:~$ 

I hope you can help me get this puppy on my desktop so I can use it.   Thanks for your attention.  I am a linux dunce but a quick learner.

---

### Post by oldfred on 2012-06-22
Someone posted before that there are fraudulent Chinese Flash drives available on the Internet. They somehow change smaller ones to report a larger size. 

Hope that is not what you have.

---

### Post by d.w on 2012-06-23
I have 100% money back no questions asked guarantee on these drives.  No problem there.  The ongoing usb projects in linux seem to be feeling the strain.  Looking at the  new threads, I would guess there is no hope foe getting the fingerprint scanner and the web cam working on this laptop. What a shame.  Oh well,  it is what it is.  THX

---

### Post by SeijiSensei on 2012-06-23
> /dev/sdb1 2920 1048575999 524286540 b W95 FAT32

Since fdisk can see the partition, maybe a little testing is in order.

First, though, the results from fdisk are a bit puzzling.  It reports having a 1 TB partition with half of it in use.  Do you already have stuff on this drive?  

Well leaving that aside for the moment, try this:

```
sudo mkdir /mnt/test
sudo mount -t vfat /dev/sdb1 /mnt/test

```

What happens?  Can you list the contents of the mounted drive with "ls -l /mnt/test"?

---

### Post by d.w on 2012-06-23
cowboy@U02B:~/Documents$ sudo mount -t vfat /dev/sdb1 /mnt/test
mount: special device /dev/sdb1 does not exist
cowboy@U02B:~/Documents$ ls -l /mnt/test
total 0
cowboy@U02B:~/Documents$ 

I have nothing stored on either of these drives. And they are Chinese...  And I do not want to waste your time.  I don't even have a wild guess at this point.  Unless you have a brainstorm. Let me say thanks to you and lets move on.  I could care less about writings drivers. OL.

---

