---
title: "weird external HDD problem"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by mab1376 on 2008-01-28
[IMG]http://mab1376.com/error.jpg[/IMG]

can anyone help.

---

### Post by chrisdeckard on 2008-01-28
You are trying to mount an external drive that was unsafely removed from a Windows computer.  The NTFS log says it is potentially unclean, so it is being safe and not mounting it so you don't risk losing data.

You can force the mount from the command line by following the instructions in the pop-up.

-Chris

---

### Post by HammerNJ on 2008-01-31
> **chrisdeckard said:**
> You are trying to mount an external drive that was unsafely removed from a Windows computer.  The NTFS log says it is potentially unclean, so it is being safe and not mounting it so you don't risk losing data.

You can force the mount from the command line by following the instructions in the pop-up.

-Chris

Hi Chris:

Question for you. I bought a Seagate FreeAgent 300GB drive in order to take off some files from an Feisty Fawn install on an IBM 3660 server. When I plugged it in onsite, the drive showed up as NTFS and un-writeable. Not knowing about ntfs-3g, I reformatted it as one, single Linux partition (from within the Ubuntu command line) and made some changes to /etc/fstab to give myself perms to write to it. That worked fine, I copied the files over, but when I got it home and plugged it into my 7.04 Lab server (Dell 1750) the directory and files were gone! So I plugged it into my XP Laptop, formatted it as NTFS, and tried to use ntfs-3g to access it. No suck luck. How do I start from scratch and make this work?

Thanks, HNJ

---

### Post by chrisdeckard on 2008-02-08
Sorry this took a while to respond.  I haven't figured out how to get the forum thinger to let me know when there is a response to a message I post.

Here are some steps:

1)  Plug the USB drive into your laptop.
2)  Type 'dmesg' at a console and see what device the new USB drive is.  Will probably be something like /dev/sdb.
3)  If Ubuntu mounted it and it shows up on your desktop, unmount the volume, but don't unplug i from your USB port.
4)  You can use the Partition Editor from the System->Administration menu, or use fdisk from the command line.  I prefer fdisk, but I'm a command line freak.
5)  Delete any and all partitions on the USB disk.  (In fdisk, use the d command).
6)  Create a new partition, and have it take up the whole space on the drive.  (In fdisk, use the n command).
7)  Now you'll need to commit your changes to the disk.  (In fdisk, use w).
8)  Now create a filesystem on the disk.  If you are going to swap this disk between Linux and Windows, you should probably use a FAT filesystem.  NTFS, while usable in Linux, is not something I'd consider stable or production quality.  It's a proprietary filesystem and has been hacked to work on Linux.  I see the only benefit of it as being able to read a broken Windows disk to recover data.

Anyway, create a new filesystem on this disk.  Again, if swapping, you FAT:

```
# mkfs.vfat -F 32 /dev/sdb1
```

or for a Linux filesystem:

```
# mke2fs -j /dev/sdb1
```

The -j option makes it create an ext3 journaled filesystem.

Hope that helps.  It's weird that you're seeing one thing on one computer, and another on another.  Might be something silly with NTFS.

-Chris

---

