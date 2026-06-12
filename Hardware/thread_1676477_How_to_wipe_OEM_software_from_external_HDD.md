---
title: "How to wipe OEM software from external HDD?"
date: 2011-01-27
forum: Hardware
---

### Post by Bartender on 2011-01-27
Good morning!

This is not, strictly speaking, an Ubuntu question, although I'd like to use these externals on our Ubuntu PC's...

My dear old Dad is on his third external HDD.  He's handed me the first two.  The externals come with pre-installed partitions containing "helpful" software that keeps loading and installing stuff and confusing him.

Since he already has backup software on the PC, I'm looking for a way to crush all existing data and partitions and reformat the danged things back to plain old blank NTFS drives.  

I've tried gparted, but gparted doesn't even see the auto-loading partition.  Only the data partition.  Windows Administrative Tools sees the first partition but won't try to access it.  The manufacturers offer various tools for download but AFAICT nothing to blast their helpful software into oblivion.

---

### Post by peculiar penguin on 2011-01-27
[Host protected area]("https://secure.wikimedia.org/wikipedia/en/wiki/Host_protected_area")? Check your dmesg output or try hdparm -N as mentioned in that article.

---

### Post by psusi on 2011-01-27
That is because it isn't a partition.  The USB device pretends it is a cdrom that has some files on it for windows to auto run, then switches over to providing access to the hard disk.  The files are in some flash memory in the enclosure, not the hard disk.

---

### Post by Bartender on 2011-01-27
> **psusi said:**
> That is because it isn't a partition.  The USB device pretends it is a cdrom that has some files on it for windows to auto run, then switches over to providing access to the hard disk.  The files are in some flash memory in the enclosure, not the hard disk.

This is exactly what one of the drives, a WD MyBook, does.  Windows sees a "Virtual CD" that tries to take over the show.  So that function isn't even on the HDD?  It's running from flash memory installed inside the box??

How annoying.  WD provides some convoluted instructions to disable (not erase) the "SmartWare Virtual CD".  Is that pretty much all you can do?

---

### Post by psusi on 2011-01-27
Yep.

---

### Post by Bartender on 2011-01-31
A quick follow-up in case anyone else runs into the same situation.  I found a coupla YouTube videos that described how to pop the more-or-less taco-shaped black plastic shell off the 1TB WD MyBook Essential.
There's a 1TB Green Drive inside, and a little PCB that plugs into the drive then interfaces with the outside world.  You know, on/off switch, data cable, power cable.

Pulled the HDD out of the case and removed the PCB.  Dropped it into a Vantec dock.  Restarted the PC with a gparted bootable CD.  Gparted couldn't even _see_ the drive when it was inside the original case.  In the dock it was picked up no problem.  What's weird is it showed up as "unallocated".  Not NTFS, not FAT.  We'd put some data on it back at my Dad's house.  Something to do with that little PCB acting as some sort of auxiliary controller??

Anyway, it was a simple matter to format the drive as one big NTFS partition.  The Green drive acted just like any other drive I've formatted and partitioned under gparted.

It's getting harder and harder to find these externals without the added auto-run shovelware and, it would appear, even hardware in the form of PCB's running the show from inside the case.  Give me a dock and a bare drive any day.

---

### Post by psusi on 2011-01-31
esata for teh winz.

---

