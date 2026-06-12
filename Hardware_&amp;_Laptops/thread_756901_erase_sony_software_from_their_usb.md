---
title: "erase sony software from their usb"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by agim on 2008-04-16
Does anybody know how I can erase the sony software off of a sony "microvault" usb drive? And before I erase it, of course, I need to know wether or not the drive will work.

I have read much about sony's penchant for rootkits. Here's a recent article [http://blogs.zdnet.com/hardware/?p=727](http://blogs.zdnet.com/hardware/?p=727)

One of the big reasons I am a linux user is the privacy and the fact that I have much more control over my computer, I'd hate to give that away just for a cheap usb drive.
Do I have to worry about this using linux, or is this mainly a windows issue?
Thanks everyone.

---

### Post by agim on 2008-04-16
bump

---

### Post by 1875 on 2008-04-16
Use Gparted to remove anypartions on the device. Repartion and format. Test device, if it works great, if not wander down to the local tech store and buy a new unbranded flash drive, they are not very expensive anymore.

---

### Post by agim on 2008-04-16
ok, finally home in front of my own computer. I just decided to plug it in and see what happened. I was able to see the sony software as three .exe files and just delete them. Maybe this will help someone else. And to the previous poster, yes, I will be more wary about what I buy.

---

### Post by AR_Kozz on 2008-04-16
I just got one of those MicroVaults too (a 2gb they were selling cheap) and I had exactly the same problem except mine would not mount at all.

I ruled out hardware defects by putting it in my ps3, which apparently supports the root software in the drive, it was able to recognize and mount it, and read and write to/from it. So it's not bad hardware...

But on my pc (gutsy, x86) mounting in gnome or pmount produces this:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I don't remember the original dmesg result but they have all been similar to this the latest:

[17180059.532000] VFS: Can't find ext3 filesystem on dev sda1.
[17180059.556000] VFS: Can't find ext3 filesystem on dev sda1.
[17180059.580000] VFS: Can't find an ext2 filesystem on dev sda1.
[17180059.604000] VFS: Can't find an ext2 filesystem on dev sda1.
[17180059.632000] ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
[17180059.656000] ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
[17180059.880000] XFS: bad magic number
[17180059.880000] XFS: SB validate failed
[17180059.904000] XFS: bad magic number
[17180059.904000] XFS: SB validate failed

that is, "can't find filesystem" and then this "magic number" stuff. This dmesg result is after repartitioning the drive into one big linux partition.


The same basic result occurs no matter what filesystem type I use, or how many partitions. It's mystifying how it worked so easy for thread starter, whereas I can't even mount the thing... and again, I know it's not the hardware

<edit> here is the relevant part of dmesg |tail for when I make a fat32 partition on the drive.

[  284.468805] FAT: invalid media value (0xb9)
[  284.468821] VFS: Can't find a valid FAT filesystem on dev sdc.

I think I'm gonna have to make my own thread about this. Looks like this is another windows-babies-only hardware.

<nuther edit> After downloading the windows formatting software from sony's support site I was able using wine to restore the drive to its initial condition. It still can't be mounted by gnome, but mounting from terminal suddenly works now, using the partition label. Just why it won't work for me with the firmware partitions deleted is still a mystery. 

Just in case anyone else has trouble after formatting a MicroVault, you can restore it with Sony's MicroVault formatting utility from [www.sony.net/Products/Media/Microvault](www.sony.net/Products/Media/Microvault). It doesn't list it there but it appears when you follow one of the links. I got it to work using the latest version of Wine.

---

