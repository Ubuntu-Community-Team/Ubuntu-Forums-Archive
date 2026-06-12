---
title: "GParted Cannot Shrink NTFS Partition"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by JordanII on 2009-04-07
So basically I'm trying to shrink my NTFS partition for a dual boot using my Intrepid CD. I've shrunk NTFS partitions many times, but this time it won't work... here's the warning I get:

[IMG]http://img187.imageshack.us/img187/5461/screenshotebs.png[/IMG]

I defragged the drive last night...


Any ideas? Thanks! :)

---

### Post by tjandracom on 2009-04-07
your ntfs partition is not cleanly unmounted. there is a mark in your partition if your last windows session is not shutdown properly. 
so you must boot to windows, check the drive/partition (using chkdsk /f) as suggested, and shutdown properly from windows.

---

### Post by dacorr on 2009-04-07
i think it is protecting the FS.

you drive states its 106GB yet actual size seems to be 111GB,

think your patition table has a bit of a headache

Run ntfsfix /dev/sda1 from terminal

you need to install ntfsprogs (sudo apt-get install ntfsprogs)

to fix the ntfs partition table

Dac

---

### Post by upchucky on 2009-04-07
and after you ran chkdsk what did it do? if you did not do the chkdsk do that first, if that fails then try this.

I am assuming that you want to repair a non booting windows from within Linux if this is true then there is a utility package in linux called libntfs it has a program called ntfsfix that will get the windows shutdown/startup problem fixed.

ntfsfix does not actually fix inconsistencies but it cleans the NTFS filesystem Journal which enables the partition to be mounted again and able to read/write with ubuntu.

Also Knoppix is an awesome repair live cd that can rescue windows systems that are taken down either by viruses or the self destruct mode that microsoft thinks should be there.

---

### Post by Mark Phelps on 2009-04-07
If your NTFS partition is Vista and you shrink it using GParted, I hope you have a Vista DVD handy to repair the partition when you're done.  If you don't, you run the risk of Vista being unbootable after the shrink.

---

### Post by coffeecat on 2009-04-07
And if you are using Vista, Vista has a neat little partition resizing tool for resizing the C: drive. You would be better off using that after you've chkdsk'd the partition.

---

### Post by larytet on 2009-04-07
SystemRescueCD can handle wide range of the problems. Small 250MB iso - download, burn CD, boot from the CD. Try to resize using the tools on the CD - graphic API.

---

