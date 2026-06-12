---
title: "(?) Installing Ubunto on an EHD"
date: 2011-01-15
forum: Hardware
---

### Post by GingerGiant on 2011-01-15
**Here's what I want:**

I want to have Ubuntu installed on an external hard drive. I run Windows XP on my laptop, and I want to have the external Ubuntu option available to protect my school work (and free up some space on the Windows side for video games :D).

**Here's what's happened so far:**

I used the Ubuntu USB Installer to "do something" to my external hard drive. When I boot from the EHD, Ubuntu runs. From there, I see an executable for the Ubuntu Installer. Any settings I change from a given Ubuntu boot are not saved if I restart (i.e., moving the shortcuts to new positions on the desktop, adding folders, etc...).

**Here's what I don't understand:**

Why does the Ubuntu Installer (after booting with Ubuntu) try to partition my Windows side? Can I partition the EHD instead?

---

### Post by ajgreeny on 2011-01-15
How did you use the Ubuntu USB Installer when you don't have ubuntu installed yet?  I think you must have a live Ubuntu on the EHD, not a full partitioned install, and as you are using that disk to run Ubuntu, and it is therefore mounted, you can not install an OS to the EHD; only your internal hard disk will be available.

If you have a flash drive that is big enough (2GB) you should "burn" Live ubuntu on to that using unetbootin, which is available for windows, I think.  You can then use the flash drive to install a full partitioned install of Ubuntu to the EHD, making sure grub is put on the EHD, probably /dev/sdb, and not on the internal hard drive, /dev/sda.

Just to be sure where we are, boot to ubuntu using whatever you have at the moment (your EHD?) and in terminal run ```
sudo parted -l
```that's a lower case L at the end, and report back here the output from that command.  That will let us see what is already on your two disks and allow us to give you better advice.

PS:  Do you have a CD drive and a live CD of ubuntu, and is that what you used to "do something" to your EHD?  If so, you can use the live CD to do a proper install of ubuntu to the EHD; you don't need the USB Installer at all; just choose the EHD using the standard installer system.

Come back again if I've got this right at last.

---

### Post by GingerGiant on 2011-01-15
I haven't used the sudo parted -l command yet, but I've taken a screen shot of what I did to get Live Ubuntu running. I circled the link to the Universal USB Installer. The website that links takes me to is ]http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/ .

---

### Post by GingerGiant on 2011-01-15
Ok, so, I did what you suggested and installed to a flash drive, and from there, installed to my external hard drive. I typed in that code, and this is what I got:

[COLOR=Navy]Model: ATA FUJITSU MHZ2160B (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  160GB  160GB  primary  ntfs         boot


Model: Best Buy Geek Squad U3 (scsi)
Disk /dev/sdb: 4032MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  4032MB  4032MB  primary  fat32        boot, lba


Model: SAMSUNG HM321HI (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  314GB  314GB   primary   ext4
 2      314GB   320GB  6303MB  extended
 5      314GB   320GB  6303MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label    [/COLOR]

The 320 GB drive is my external hard drive.

---

### Post by GingerGiant on 2011-01-15
I do not have a live CD of Ubuntu. I just have an EHD and USB.

---

### Post by GingerGiant on 2011-01-15
Bump!

---

### Post by ajgreeny on 2011-01-16
Try removing the USB flash drive, but leave the EHD connected, and reboot,

Grub menu should appear and give you the option of booting to either ubuntu or windows.

If there is still a problem come back once again and let's see what else is needed.

---

