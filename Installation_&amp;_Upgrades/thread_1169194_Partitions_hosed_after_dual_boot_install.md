---
title: "Partitions hosed after dual boot install?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by unnngh on 2009-05-24
I just downloaded and installed 9.10 on an HP dv2000 notebook.  I did a dual boot setup with an existing Vista home partition.  Everything is working with both OSes, but I'm not sure I understand what happened with my partitions.

First, I resized the Vista partition from ~133 GB to 90 GB, leaving me about 40 GB free for Ubuntu.

On the partition setup screen during install, the "side by side" option was selected as default, so I chose that.  It went ahead with the install and everything completed normally.

When I booted into Windows, it did a checkdisk and said something about reallocating space (didn't catch the full message).  Now, Windows thinks it still has the full 133 GB at its disposal. 

Since everything is still running happily, I'm not sure whether I have a problem or not.  Is my drive going to be hosed once I write past the 90GB that I allocated to the Windows partition?  Should I restore from the recovery disk and reinstall, or will the two OSes somehow continue to peacefully coexist?

Many thanks...

---

### Post by cariboo on 2009-05-25
Which tool did you use to resize the partition? It is recommended to use the Vista disk management tools to resize the partition.

---

### Post by lavinog on 2009-05-25
Are you sure you are using 9.10 and not 9.04?

In ubuntu:
you can list your partitions by entering this in a terminal:
```
sudo parted -l /dev/sda
```
You can post the output here.

There is also a tool called gparted that gives you a graphical view.
It isn't installed by default so you have to install it with synaptic, but once installed it will be in the menu as System>Administration>Partition Editor.
It won't let you make any changes to a mounted drive though.

---

### Post by unnngh on 2009-05-25
Thanks; here's the output from parted; if I'm reading it right, my ubuntu partition is only 2.5 GB in size? I started getting errors later on last night that the partition was full, that would explain why...I think I should be able to wipe the existing install, shrink the large block again and try again, no?  I did use the vista partition manager to do it originally.

edit: yes you are right, I got 9.04

Model: ATA SAMSUNG HM160HI (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  145GB  145GB   primary   ntfs         boot 
 3      145GB   147GB  2681MB  extended                    
 5      145GB   147GB  2500MB  logical   ext3              
 6      147GB   147GB  181MB   logical   linux-swap        
 2      147GB   160GB  12.8GB  primary   ntfs

---

