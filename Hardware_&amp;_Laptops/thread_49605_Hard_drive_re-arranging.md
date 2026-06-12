---
title: "Hard drive re-arranging"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by sizzam on 2005-07-17
I have two hard drives:

[Drive 1]
hda1 =  /  
hda5 = swap

[Drive 2]
hdb1 = /home


I think Drive 1 is about to die, it's making some not-so-good noises.   What is the best way to get all the data from Drive 1 onto Drive 2 (also keeping my /home folder in tact) so that Drive 1 can be eliminated?

---

### Post by emperor on 2005-07-17
Newbe easy way is to use Partion Magic 8.

Another way is to boot with a "rescue disk" or the "LiveCD" and then use a linux partion tool like "parted" to shrink /home (if necessary) and create new partions on hdb. The partions should not be mounted when you resize and create new ones. You will also need to install grub on hdb. There should be other discussions in the forum and good instructions concerning this issue.

---

### Post by varunus on 2005-07-17
Well, there's a howto in the tips and tricks section on making a "tar" backup.  You could back up everything as per that howto (and exclude your home folder, they describe how to do it) and then make a new partition on drive two, and then extract the backup there.

---

### Post by mungbean on 2005-07-17
During installation the Hoary auto-partitioning  didn't work for me so I used SystemRescueCD instead [ [http://www.sysresccd.org/](http://www.sysresccd.org/) ] which worked great.

This is a bootable Linux CD (Gentoo-based) that's designed for helping with disk problems etc.    List of tools from the site:

    * GNU Parted  is the best tool for editing your disk partitions under linux
    * QtParted is a Partition Magic clone for Linux.
    * Partimage is a Ghost/Drive-image clone for Linux
    * File systems tools (e2fsprogs, reiserfsprogs, xfsprogs, jfsutils, ntfsprogs, dosfstools): they allow you to format, resize, debug an existing partition of your hard disk
    * Sfdisk allows you to backup and restore your partition table

If you wanted to re-partition the newer drive and then clone the old partition onto it, QTpartman and Partimage sound like they will do what you need.  

I got the CD for  QTpartman which is a graphical program like partition magic - very easy to use.  For my installation it was just what I needed to reduce the size of the pre-installed windows partition. Then when I ran Ubuntu installer again, it found the free space and set up swap and an ext3 file system automagically.

If there's space on the Ubuntu install CD it would be a great idea to have QTpartman on there in future versions....

---

