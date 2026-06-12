---
title: "Dell 1525 with Hardy and a 1.5T in USB toaster"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by csy33delight on 2009-04-08
I am trying to set up my Dell 1525 laptops with Hardy. I tried Intrepid but could never get Skype or Google Earth to work. I loaded 8.04.2 desktop and everything seems OK. When I plug an external 1.5 terabyte drive in USB toaster, it is not seen.

What I have tried so far:

I tried both ext2 and NTFS formated disks in the toaster. Neither work.

I have a 250 gig ext2 USB disk. It works.

I have a 300 gig NTFS USB disk. It works

One 1525 is configured as a dual boot with Hardy and XP. All disks are recognized by XP.

One 1525 is setup from the disk downloaded from dell and updated. It exhibits the same characteristics as the dual boot from the Ubuntu 8.04.2 Desktop setup disk.

One 1525 still has Intrepid installed. It recognizes and auto-mounts all disks.

I have an eSATA card for the laptops.  The toaster, using eSATA instead of USB, works with both ext2 and NTFS formated disks on Intrepid. But not on either Hardy installation.

If I use gparted on Hardy to look at the NTFS formated 1.5T disk, it shows /dev/sdb (1.36 TiB) as NTFS and a /!\ with information of "Unable to read the contents of this filesystem". If I look at the ext2 formated 1.5T, it shows the file system, Label, Size, Used, and Unused correctly.  When I try to mount it (Places -> Computer -> USB Drive) it says can't mount file.  

I am at a loss as to where to go from here. Thanks in advance for help.

---

### Post by Sam Lars on 2009-04-09
If Intrepid works fine, it may be due to its software being newer than in Hardy.

---

### Post by csy33delight on 2009-04-09
Obviously. How do I debug Hardy? Hardy is LTS and supplied by Dell as an option. Is a 1.5T drive too big for Hardy? Since the smaller drives work fine, the USB detection and auto-mounting is working. Since the 1.5T works in XP and Intrepid, it is not a hardware issue with the 1525.

It has to be some sort of a software issue between the Hardy installation and the Seagate drives.

I would like to use Intrepid, but cannot see booting into XP in order to use Skype and Google Earth. Hardy is the version which Dell supplies on the new 1525's that they ship with Linux.

Since Intrepid works, whatever the issue is, it has been resolved. I need to find out what I need to install or update to get Hardy working properly.  Can someone point me in the right direction?

---

### Post by csy33delight on 2009-04-10
I figured out a work around:

Use:
sudo blkid
To get UUID and File Type for each disk, For example:
/dev/sda1: UUID="54FCCE62FCCE3DCC" TYPE="ntfs" LABEL="TRANSPORT" 

Make a folder to mount the disks:
sudo mkdir /media/Storage

Add entries at the end of fstab for each disk:
sudo gedit /etc/fstab

For Example:
#Transport disk
UUID=54FCCE62FCCE3DCC /media/Storage ntfs defaults,users,unmask=000 0 0
#0-9 A-J storage disk
UUID=4255f863-48c0-4a99-9ddc-a5c6bd603997 /media/Storage ext2 defaults,users 0 0
#K-Z storage disk
UUID=6fe15516-0c9d-4c3f-a347-f6e752d85b6d /media/Storage ext2 defaults,users 0 0

This allows me to plug any of the 1.5T drives into the toaster and they are recognized at boot time.

If I need to swap drives without re-booting, I unmount the old drive and then "sudo mount -a" to mount the new one.

I still do not know why these drives do not automount like the smaller USB drives do.

---

