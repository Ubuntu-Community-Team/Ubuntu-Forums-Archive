---
title: "General insructions on using an external hdd?"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by plamen_todoroff on 2008-01-29
I'm looking for some general instructions on how to use correctly my external usb hdd. It's partitioned in 14 partitions (one of them, sdb1, is ntfs). All of them are mounted automatically when i plug it in and nautilus opens 14 new windows, showing the contents of each partition. So far so good.

What do I do if I want to disconnect the usb drive? Just pull out the cable? Is there something like "safely remove hardware", like in Windows? I've read many howto-s about unmounting an external hdd, but they all were about usb hdd-s that have just one partition (and in all the tutorials this partitions was refered as "the drive", like "...unmount the drive /dev/sdb1"). Also some tutorials say to "eject the drive" with some right-click option which i don't have. What is the thing to do when I want to disconnect my usb hdd?

There's also a problem that I have about this usb hdd. When I boot my Ubuntu 7.10 with the usb hdd connected, the boot process freezes at "loading hardware drivers", so I have to shut it down with the power button, disconnect the drive and then it boots ok. When I'm in the desktop i plug it in and everything's ok. For the last week I've been shutting down Ubuntu (to unmount the usb drive), then I disconect the drive, and then boot ubuntu again. It just doesn't feel right.

Sorry for my english. Any help is greatly appreciated.

---

### Post by ellis rowell on 2008-01-29
> **plamen_todoroff said:**
> I'm looking for some general instructions on how to use correctly my external usb hdd. It's partitioned in 14 partitions (one of them, sdb1, is ntfs). All of them are mounted automatically when i plug it in and nautilus opens 14 new windows, showing the contents of each partition. So far so good.

What do I do if I want to disconnect the usb drive? Just pull out the cable? Is there something like "safely remove hardware", like in Windows? I've read many howto-s about unmounting an external hdd, but they all were about usb hdd-s that have just one partition (and in all the tutorials this partitions was refered as "the drive", like "...unmount the drive /dev/sdb1"). Also some tutorials say to "eject the drive" with some right-click option which i don't have. What is the thing to do when I want to disconnect my usb hdd?

There's also a problem that I have about this usb hdd. When I boot my Ubuntu 7.10 with the usb hdd connected, the boot process freezes at "loading hardware drivers", so I have to shut it down with the power button, disconnect the drive and then it boots ok. When I'm in the desktop i plug it in and everything's ok. For the last week I've been shutting down Ubuntu (to unmount the usb drive), then I disconect the drive, and then boot ubuntu again. It just doesn't feel right.

Sorry for my english. Any help is greatly appreciated.

You seem to be having a lot of trouble. I use a USB HDD, it has 3 partitions. To unmount it (or eject) you need to put the pointer on the icon then right click ( this has to be done for each partition in turn) which should open a window giving you the choice to unmount or eject. If you do not unmount a disk or key drive, any thing which you have saved to it will not appear when re-mounted. I have this problem with a key drive which I use to transfer files from a Ubuntu machine to a Windows machine. With 14 Partitions you definitely have a problem.

---

### Post by plamen_todoroff on 2008-02-06
Ok. Let's forget the number of partitions I have. I reformatted the drive and now it has 6 partitions. It won't boot (as described in my first post) either, ubuntu gets stuck at "loading hardware drivers).

Some new information for you guys that might be useful: with the usb hdd connected even the gparted livecd couldn't boot, it gets stuck with loading wm-raid (or something similar :oops:). I have the feeling that my internal hdd and external usb hdd are treated as some kind of raid configuration by ubuntu and also by the gparted livecd.

I just want to be able to keep my usb hdd always connected. Now I have to boot without it and when the desktop shows i plug it in.

Anybody? Please?

---

