---
title: "Question regarding Windows Vista and Ubuntu"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by phi204 on 2009-01-26
Hello all,

Here's the situation, on my laptop i currently have windows vista installed and I want to partition my HD so that I can install ubuntu on it. I don't want to lose my windows vista or all my data within it(*THIS IS KEY*).

Several questions come to mind when I think about doing this...

1 - How exactly does this work after it is done, does it ask me which partition I want to boot from each time? Will have to be constantly going in and out of the BIOS if I want to flip back and forth between OS's? (not instantly, after a restart of course)

2 - I downloaded the Ubuntu 8.10 iso and I am currently wondering does this have GParted on it already when I boot this thing up from the CD (before I actually install the OS)? 

3 - If I use GParted to make my ubuntu partition am I creating a "logical partition" and I know for windows the second option you select for that designated partition is "ntfs", but what do I select for ubuntu?

Any tips/suggestions/comments would be greatly appreciated!

Thanks in advance!

phi

---

### Post by taurus on 2009-01-26
Have a few links for you to look over.  And before you start anything, BACK UP your files.  And don't forget to defrag your harddrive a couple of times first before you resize it with gparted.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)
[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)

---

### Post by Arcesso on 2009-01-27
In a nutshell as I understand it:

1.  The grub boot loader will let you choose your OS that you boot into.  So no BIOS for you!  

2.  Ubuntu as I understand it does have Gparted accessible when booting from the live cd.

3.  NTFS I think would be a bad choice for a linux install.  Ext3 is the standard but there is Ext4 which I have yet to explore.  Ubuntu can read and write to NTFS but windows without the proper software cant read or write extX.  So for both to use data you will have to keep it within windows, make a 3rd data partition, or get the software for windows to read ext file systems.

Also, I would back up everything you cant live without before going though the operation of course.

Hope that helps... :D

arc

---

### Post by Mark Phelps on 2009-01-27
Since keeping your Vista intact is important to you, unless you have a Vista DVD, do NOT use ubuntu or GParted to resize your Vista partition; instead, use the Vista disk manager to shrink it.  If you need some advice on how to work around Vista resizing problems, see the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

This is because, sometimes, using non-Vista tools to shrink a Vista partition results in the partition being unbootable -- which is easily fixed if you have a Vista DVD. But if you don't, it renders your Vista unbootable and you've effectively lost use of it.

---

