---
title: "USB Powered HDD not recognised"
date: 2012-05-10
forum: Hardware
---

### Post by captainKrash on 2012-05-10
Hi All,

I recently purchased an Intenso 640gb USB powered HDD with the intention of backing up my data on my 10.04 desktop machine, so that I can upgrade to 12.04. My expectation was that I could plug this USB powered drive in, it would appear like a USB stick does and I could get about copying my data across.

Anyhow, that did not happen.

I have had a search on the forum and I am none the wiser; this is what I have done - which hopefully will provide some pointers:

```
x@x-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 04f2:0116 Chicony Electronics Co., Ltd KU-2971 German Keyboard
Bus 002 Device 005: ID 192f:0416 Avago Technologies, Pte. 
Bus 002 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 13fd:1840 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
x@x-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e607b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59583   478600416   83  Linux
/dev/sda2           59584       60801     9783585    5  Extended
/dev/sda5           59584       60801     9783553+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13d053b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625128288+   c  W95 FAT32 (LBA)

``````
[38026.690753]
x@x-desktop:~$ dmesg | tail -n 20
 usb 1-2: new high speed USB device using ehci_hcd and address 8
[38026.841176] usb 1-2: configuration #1 chosen from 1 choice
[38026.841463] scsi7 : SCSI emulation for USB Mass Storage devices
[38026.841641] usb-storage: device found at 8
[38026.841643] usb-storage: waiting for device to settle before scanning
```If anyone has any ideas, I'd appreciate it.

---

### Post by underquark on 2012-05-10
It may be a hardware problem. I was unable to access a particular USB-powered external drive from one machine but could access it from another machine. Both machines running ubuntu 10.04. USB current output is sometimes not quite enough to power an external hard drive. You can get double-plugged USB cables that draw power from two ports but transfer data through only one.

---

### Post by captainKrash on 2012-05-10
Thank you for your reply. This one has a twin usb cable, I will try the back ports on the machine and perhaps try it on my laptop. Thank you.

---

### Post by captainKrash on 2012-05-10
Not detected on Laptop or other usb ports to rear of desktop machine.

Pants.

---

### Post by QIII on 2012-05-10
Are you plugging it in before or after starting the computer?

---

### Post by ahallubuntu on 2012-05-10
For fun, fire up Gparted and see if you can see the main partition on the drive (/dev/sdb).  If you can, delete the existing partition and format it for ext4 instead of FAT32 (which is limited - for one, you can't have any files larger than about 4.1GB on a FAT32 partition).  If you will ever use this drive with Windows, NTFS is probably a better option than ext4.  

After that, see if you can access the drive - because clearly fdisk can see it...

---

### Post by captainKrash on 2012-05-10
Plugging in after starting machine.

Just tried on win7 machine and it sees the drive FAT32.

I don't have much experience with Gparted...do you mean the live CD or app within ubuntu?

---

### Post by captainKrash on 2012-05-10
Just rebooted machine and had it plugged in from off - no change - still not seen.

---

### Post by Andrew_P on 2012-05-10
> **captainKrash said:**
> I don't have much experience with Gparted...do you mean the live CD or app within ubuntu?

There are flaky versions of GParted that simply don't work, including the one supplied with Ubuntu.  Download a copy of the ISO for SystemRescueCD 2.5.1 or later, burn it to a CD, then boot the machine with this CD.  I've used it to wipe the master boot record and all partitions on a second-hand SATA hard drive from a Windows NT server, where the normal tools supplied with Ubuntu were useless.  If you can connect the USB drive to a machine that at least recognizes the drive and has enough power for it to spin the discs, SystemRescueCD should be able to operate on it.

Also, you might check the drive specification to be sure the USB port is capable of powering it.  Some USB devices require external +5V power from a "wall wart" power supply and have an external supply jack for this purpose.

If the USB drive was assembled in Taiwan or China, there's also the possibility that the USB interface is cr*p.  I've had to return USB devices that absolutely refused to work on Linux and Windows 98, and only partially worked on Windows XP.

---

### Post by ahallubuntu on 2012-05-10
Well, I meant the Gparted app within Ubuntu - it's the same app you can run from its own live CD or many other live CDs like Parted Magic.

---

### Post by ahallubuntu on 2012-05-10
> **Andrew_P said:**
> There are flaky versions of GParted that simply don't work, including the one supplied with Ubuntu.


Funny, I've been using Gparted successfully in Ubuntu for years.  It is important to do updates and get the latest version should a bug be present in the release version from the install.

---

### Post by captainKrash on 2012-05-10
I updated gparted in ubuntu and it did indeed see the drive. I deleted the partition and then created new ext4 filesystem in all the free space.

Now I have a recognised drive - BUT no perms to put anything in it. 

Am I being a bit dim?

---

### Post by ahallubuntu on 2012-05-10
You probably need to set permissions for your account rather than the root (sudo) account.  I'm a terminal guy so I'll tell you how to do it that way.  Open a terminal and type:

sudo chmod -R 777 /media/name-of-drive/

(replace "name of drive" with whatever yours is - maybe a long number which is the UUID of the partition).

Note that this gives EVERYONE permission to read/write files on your system.  It's a bad idea if you will ever be sharing this drive, but if you are the only person who will ever use it, no worries.

FYI, if you have a goofy name for "name of drive" you can add a human-readable label like "MyExternalDrive" in Gparted, so it will always show up with a friendly name when you plug it in.

---

### Post by captainKrash on 2012-05-10
Well , thank you to everyone who replied. I have gone from thinking that I would have to return the drive faulty to having a fully functioning drive!

Really appreciate the help! Looking forward to trying out 12.04 on the actual machine rather than the live cd.

---

