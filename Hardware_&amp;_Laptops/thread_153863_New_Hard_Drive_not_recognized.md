---
title: "New Hard Drive not recognized"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by KeithO on 2006-04-01
I just did a fresh install of Breezy and during the install it recognized the two hard drives I have in my machine (40 gb and 250gb).  I installed on the 40 gb hd just fine however when Breezy is running, it does not see the 250 gb hd at all.  Searching didn't bring up anything.  BIOS does recognize the 250 as set to slave so thats all good. 

Any ideas?

---

### Post by aysiu on 2006-04-01
What filesystem is this second drive? NTFS? FAT32? Ext3?

---

### Post by KeithO on 2006-04-01
brand new hard drive.  just bought it today.  goal is to make it a storage for file sharing.

---

### Post by MacV on 2006-04-01
Did you format it, or did it come already formatted? To be safe, I'd get an fdisk floppy and make some partitons to format.

---

### Post by KeithO on 2006-04-01
i hadn't had a chance to format it.  i want it in ext3 but ubuntu needs to see it first.  its a WD.  not sure if they preformat.

---

### Post by TTT_travis on 2006-04-01
[QUOTE=KeithO]i hadn't had a chance to format it.  i want it in ext3 but ubuntu needs to see it first.  its a WD.  not sure if they preformat.[/QUOTE]

Check the little jumpers and make sure you have it setup master slave first, then use either FDISK or even easier your ubuntu install cd to format it as a ext partition. then under linux do 

mount -t ext /dev/hdb1 /mountpointhere

or something similar depending on the setup.

---

### Post by KeithO on 2006-04-02
I swapped out the ide cables and installed ubnutu on the new hd.  i was then able to wipe it and do what i needed.  thanks!

---

### Post by KeithO on 2006-04-07
Ok. i have another issue related to this.  For some reason the second hard drive will not keep open privileges.  I'm the only one using the computer and would perfer not to have to chmod it every day i need to write to this hard drive.

---

### Post by KeithO on 2006-04-08
bump

---

