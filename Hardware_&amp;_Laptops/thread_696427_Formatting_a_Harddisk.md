---
title: "Formatting a Harddisk"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by jerksire on 2008-02-14
I had a 40gb hard disk with 2 partitions .One had Windows and the other Ubuntu .
I got a new hard disk for Ubuntu but I'm unable to format the  old disk which had a Ubuntu. How do I go about doing this?

---

### Post by yabbadabbadont on 2008-02-14
What happens/what error messages are displayed when you try to format it?

What, **exactly**, is the command you ran when trying to do this?

---

### Post by jerksire on 2008-02-22
I just don't know how to go about it as I'm new to Linux .This is my first hard drive to format in Linux so I don't know where to start.

---

### Post by chrisdeckard on 2008-02-22
Are you trying to reuse the old disk under Windows again, or to use the old Ubuntu partition under Ubuntu, but as other storage?  Did you install Ubuntu on the new disk?  You need to provide more information as to what you're trying to do to adequately help you.

-Chris

---

### Post by Ampi on 2008-02-27
It looks like I have the same problem, I think.
So I'll explain mine...

I have two harddisks, one with Ubuntu (hdb) and one with Fedora (hda). 
What I want to do is format the harddisk that has Fedora so I can use it as a storage device for Ubuntu.

I have no idea how to do that. I guess I'll have to format it first so let's start with that, how do I do that?

---

### Post by gali98 on 2008-02-27
sudo apt-get install gparted

it will be in adminstration tools where synaptic is.

Kory

---

### Post by Namain on 2008-02-27
> **Ampi said:**
> It looks like I have the same problem, I think.
So I'll explain mine...

I have two harddisks, one with Ubuntu (hdb) and one with Fedora (hda). 
What I want to do is format the harddisk that has Fedora so I can use it as a storage device for Ubuntu.

I have no idea how to do that. I guess I'll have to format it first so let's start with that, how do I do that?

Step 1: Install gparted.  This is a graphical partition editor that uses the GNU Parted partition editor to work.  To install go to a command line and type:
```
sudo apt-get update && sudo apt-get install gparted
```

and then hit enter.  Apt will install gparted.

Step 2: Go to System --> Administration --> Partition Editor.  This will start gparted.  It will scan all of the hard drives that you have connected and display their partition tables.  Depending on your configuration, this could take a while.

Step 3: Use the drop-down menu on the top-right, to select the drive you want to edit.  GParted will normally default to the drive you booted off of.

Step 4: Modify the partitions as you like, just remember that you MUST hit the "Apply" button before any changes are written to the disk.

Step 5: Now that you've played with the partitions, you should reboot to make sure your computer scans for the drive.

Step 6: Check Places --> Computer to see if your drive is recognized by Ubuntu.  If not, you can mount it manually by running regular mount commands:
```
mount /dev/hda1 /mnt
```
Where hda1 is the partition you are trying to mount and mnt is the directory you are mounting the drive to.

---

### Post by Andeh on 2008-03-11
is there a way to name Hard Drives in linux?

---

