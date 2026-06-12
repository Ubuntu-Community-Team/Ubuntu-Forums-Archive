---
title: "Reformat ext* space"
date: 2008-08-10
forum: General Help
---

### Post by OsamaK on 2008-08-10
Hello!

I have installed Ubuntu 8.04 on my laptop. Now, I'm planning to sell my laptop, for that reason, I want to restore my ext* space and reformat my hard disk into NTSF format to get all space from Windows.

Is there any tools on Ubuntu\Windows doing that? How to?

---

### Post by cdtech on 2008-08-10
Gparted Live CD.....

---

### Post by Elfy on 2008-08-10
If you have resized the partition to install ubuntu and still have windows installed. Before you remove ubuntu you need to use your win disc to fix the boot in it's recovery console.

Once you have done that and you can see that windows boots ok, reboot with the buntu livecd and use the partition editor in sys > admin menu to delete the ext3 and then either make a new ntfs partition or resize the existing one.

---

### Post by OsamaK on 2008-08-10
I resized my hard-disk, and Windows boots well. I don't think I have to use Microsoft's Recovery Console, no?

Anyways, I tried livecd: System > Administration > Partition editor, and I got this problem:

```
Unable to delete /dev/sda6!
Please unmount any logical partitions having a number higher than 6
```

I tried right-click on /dev/sda6 > Unmount Volume , but the problem wasn't solved. Anyideas?

---

### Post by Elfy on 2008-08-10
It's probably the swap - run this in a terminal

```
sudo swapoff -a
```

then try again, delete the partitions inside of the extended partition first.

---

### Post by OsamaK on 2008-08-10
What about:
ubuntu@ubuntu:~$ sudo swapoff -a
swapoff: /dev/sda7: Cannot allocate memory

---

### Post by Elfy on 2008-08-10
Maybe it's not mounted then - if it doesn't let you delete the partitions in reverse order - sda9, sda8, sda7, sda6 etc can you post a screenshot of gparted - please use the attach tool

---

### Post by Bucky Ball on 2008-08-10
When you installed windoze, you get to the part where you choose where you want to put it. It also give you the option to delete/create drives. Delete everything so the whole disk in unallocated (unpartitioned) space. Make a partition for Windows, partitions for data and off you go. Will wipe and format and install.

Can't see how you can delete Ubuntu from inside Ubuntu. How can it delete the partition it is running on? If anyone can explain, I'm curious ... :)

---

### Post by Elfy on 2008-08-10
> Anyways, I tried livecd:)

Windows is already installed afaik - justtrying to get ext3 and swap space back

---

### Post by OsamaK on 2008-08-10
This is my GParted shot.

---

### Post by bigbrovar on 2008-08-10
what in did in my case was to put in a live cd ... go to System/Administration/Partion Editor

which would open ope gparted .. from there delete every partition there which would make them raw partitions whichout a filesystem.. now u can then .. slot in ur windows and install it ... u you already dual boot qith windows and would only want to delete the ubuntu partition .. then just boot into ur windows  and go into Disk Management - right-click My Computer, Manage, Disk Management. from there u would see all the partitions u have on your system .. right click and delete the ubuntu partition .. then format it into NTFS .. hope that helps ..

---

### Post by Elfy on 2008-08-10
right click sda7 and unmount then you should be able to delete sda7,6,5 and sda3


Edit - you are doing this in the livecd?

---

### Post by Bucky Ball on 2008-08-10
In Windows;

[quote=bigbrovar]go into Disk Management - right-click My Computer, Manage, Disk Management.from there u would see all the partitions u have on your system .. right click and delete the ubuntu partition[/quote]Hmm, not sure about this. Yes, Windoze will see the patition, but you will notice there is no detail whatever apart from 'Healthy'. Windows does not acknowledge EXT3 format (without dodgy software to do so) and I would be dubious about this approach. If you have actually done it, then I stand corrected. But in my experience, no. :0)

---

### Post by OsamaK on 2008-08-10
> **forestpixie said:**
> right click sda7 and unmount then you should be able to delete sda7,6,5 and sda3


Edit - you are doing this in the livecd?

They're all unmounted, See my 'Computer' shot.

Yes, I'm on a livecd.

---

### Post by Elfy on 2008-08-10
If the partitions you are trying to delete no longer have the key symbol in gparted then you should be able to delete them. Your screenshot of gparted shows 3 mounted partitions.

If they are no longer mounted and you still can't delete them then maybe do it from the terminal using fdisk - but I've never used it myself.

This post gives some information on using fdisk as does it's man page

[http://ubuntuforums.org/showpost.php?p=2901984&postcount=6](http://ubuntuforums.org/showpost.php?p=2901984&postcount=6)

---

