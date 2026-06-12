---
title: "[SOLVED] How do I partition and format a new [SATA] HDD?"
date: 2008-06-01
forum: Hardware
---

### Post by bilijoe on 2008-06-01
I recently installed a new (i.e., unpartitioned, unformatted) 250 Gb Segate SATA HDD.  The Device Manager sees it, and lists it as "/dev/sdb", but it shows up nowhere else that I can find.  Once it it properly set up, I want to use it as my primary (probably only) drive, so I will need the partitions basic "volume", "volume (ext3)" (what is that used for, BTW?), and "volume (swap)" (which seems to never get used, as I have 4 Gb memory installed), and I want to use a separate partition for my home directory, as so many people have recommended.  So, how do I go about partitioning and formatting the drive, so the rest of the system will recognize it?  And, will I have any trouble booting from an SATA device?

---

### Post by tamoneya on 2008-06-01
shouldnt be any problems.Just install gparted.  The GUI is very simple.```
sudo apt-get install gparted
sudo gparted
```

---

### Post by bilijoe on 2008-06-01
> **tamoneya said:**
> shouldnt be any problems.Just install gparted.  The GUI is very simple.```
sudo apt-get install gparted
sudo gparted
``` Thanks.  That part was easy.  Now's the part where I have to admit I don't really know what I'm doing.  I assume I have to set up at least 3 partitions, one for the OS and generic stuff, an EXT3 partition (whatever that is?), and a swap partition.  If I am also going to set up a partition for my "home" directory, how large should I make the "main" partition, the EXT3 partition, and the Swap partition (I have 4 Gb of RAM)?

---

### Post by housam on 2008-06-01
> **bilijoe said:**
> I recently installed a new (i.e., unpartitioned, unformatted) 250 Gb Segate SATA HDD.  The Device Manager sees it, and lists it as "/dev/sdb", but it shows up nowhere else that I can find.  Once it it properly set up, I want to use it as my primary (probably only) drive, so I will need the partitions basic "volume", "volume (ext3)" (what is that used for, BTW?), and "volume (swap)" (which seems to never get used, as I have 4 Gb memory installed), and I want to use a separate partition for my home directory, as so many people have recommended.  So, how do I go about partitioning and formatting the drive, so the rest of the system will recognize it?  And, will I have any trouble booting from an SATA device?

As tamoneya advised you, Gparted will do the job smoothly. 
ext3 is the format system where ubuntu want to be installed on.
swap ( the vertual memory )is needed for hybernation , heavy games and during the downloads. for your case , swap = RAM is ok.

so you can partition your hard ( only ubuntu installed )
- 10-15 GB ext3 format for the root ( / )
- 4 GB for the swap
- the rest ext3 format for  /home partition

---

