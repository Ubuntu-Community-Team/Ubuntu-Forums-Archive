---
title: "Bad sectors on harddrive"
date: 2011-04-11
forum: Hardware
---

### Post by Melpomene on 2011-04-11
I have a problem with a harddrive that was a part of a raid (complete duplicate). 
It got an error from my Torrent program saying that it was unable to write to the disc due to Input/ouput -error. 

When I open the Ubuntu built in hard drive administration panel the disc has a green light but the SMART- status claims that the disc has a few broken sectors. 

What does this mean and how do I fix it? 

I have unmounted the disc and I have run "badblocks" on the drive. It took almost 100 h to complete but now it is done and it did not find any errors. 

I've also tryed running

sudo fsck /dev/sdb

but it told me I had a bad super block and that it tryed with a reserve block but this also seemed to fail and it suggested I'd run: 

sudo e2fsck -b 8193 /dev/sdb

but this gave the same output. 


How do I fix the bad sectors?

---

### Post by PapaNerd on 2011-04-13
If you don't care about the data on the disk, you could wipe it clean with something like the [http://sourceforge.net/projects/disc-wipe](http://sourceforge.net/projects/disc-wipe) utility.  This writes patterns across the disk and the firmware should identify bad sectors and write them into the bad sector table.  You'll then need to use fdisk or gparted to write a new disk label and create the partition(s) you want.

---

