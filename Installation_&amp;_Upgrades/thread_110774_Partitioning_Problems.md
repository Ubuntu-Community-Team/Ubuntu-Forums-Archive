---
title: "Partitioning Problems"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by Hakujin on 2005-12-31
Hello, first time posting here.  If I should post this in a more appropriate section please point me in the right direction.

I am attempting to resize my laptop WinXP NTFS Partition (80GB) so that I can dual boot with Ubuntu.  My problem occurs when I select resize current partitions within the Ubuntu installer.  The minimum partition size it will allow me to create is 41GB (51% of my drive!).  I don't need more than 5GB for my linux install - I would prefer the other 36 in my NTFS partition.

I've installed Linux quite a few times on other computers, this is my first attempt on my laptop.  Any suggestions? Thanks in advance.

-Colin

---

### Post by earobinson on 2005-12-31
you should be able to change this in the advanced partition section

EDIT: this is the correct place for this question

---

### Post by az on 2005-12-31
[QUOTE=Hakujin]  My problem occurs when I select resize current partitions within the Ubuntu installer.  The minimum partition size it will allow me to create is 41GB (51% of my drive!).  I don't need more than 5GB for my linux install [/QUOTE]


Are you taking the default action offered by the partitioner to rezise existing partition?  If so, you should be able to backspace the offered size and just type 5G.  I found it confusing the first time.  I did not know if it was asking me the size of the new partition or the size to leave the old partition when asked "partition size".  Thinking about it (not being in front of my computer) I am still not sure.... :p

---

### Post by Sef on 2005-12-31
I) If there is no free space on the disk, do this:

A) Highlight the partition you want to shrink.  

B) Highlight the disk size.  

C) Erase the numbers on the screen and write in the new size of the partition -  XX.X GB .   

                 - Don't forget to put GB

4) Click on the button.  (I think it says 'OK'.)
 
5) Then click on 'Done Partitioning This Disk' (or something similiar, it's the top option.)

II) Two Partitions Now

A) One which says NTFS and one that says Free Space.

        1) NTFS is the XP partition
        2) Free Space can used to set up Ubuntu Linux.

            -) It's a good idea to maually partition, and set up a /home directory, so when you upgrade Ubuntu, your files and settings won't be overwritten.

---

### Post by Hakujin on 2005-12-31
Got it working, thanks. I ended up doing what Sef suggested after mucking around in the partition utility.  You have to shrink the existing partition first then it works wonderfully. (I assumed that it would do this for me.) The help is much appreciated.

-Colin

---

