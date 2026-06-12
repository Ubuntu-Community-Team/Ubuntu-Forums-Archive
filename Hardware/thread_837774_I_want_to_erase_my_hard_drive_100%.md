---
title: "I want to erase my hard drive 100%"
date: 2008-06-22
forum: Hardware
---

### Post by david5432 on 2008-06-22
I want to completly get rid of ubuntu and use a XP disk to get windows back. How do i go across this?

---

### Post by tamoneya on 2008-06-22
just pop the windows disk in and boot it.  Then when you get to the partitioner setup you just delete all the partitions and tell it to install into the unpartitioned space.

---

### Post by david5432 on 2008-06-22
It tells me that there is no hard drive installed.

---

### Post by bobbob1016 on 2008-06-22
Just put the XP CD in, and delete all the partitions it shows.  It shouldn't have a problem deleting the Ubuntu partitions.  Microsoft even has a technote on this, [http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458) .  If you want to shred your data, as in you are getting rid of the HD, burn this [http://dban.sourceforge.net/](http://dban.sourceforge.net/) to a CD, and boot from it.  Type "autonuke" at the first prompt, it takes a while, but completely shreds your data.

EDIT:  If it's saying no HD is installed, that is, probably, a completely different issue.  The HD could be going bad or something.

---

### Post by tamoneya on 2008-06-22
are your harddrives sata drives.  If they are you probably need to enable them for compatibility mode which is done in the bios.

---

### Post by david5432 on 2008-06-22
It doesn't work. It does not give me any options when it loads from the disk. it goes straight to ubuntu. the file is a .iso file. Is that right "dban-1.0.7_i386.iso" is the file name. Do I have to do anything to it before it will run properly?

---

### Post by tamoneya on 2008-06-23
you enable compatibility mode in the system BIOS.  To do this you hit F2 or F10 or Delete on the prompt.  It is the first or second screen you see in the boot process.

---

### Post by david5432 on 2008-06-25
bump

---

### Post by logos34 on 2008-06-25
> **david5432 said:**
> It doesn't work. It does not give me any options when it loads from the disk. it goes straight to ubuntu. the file is a .iso file. Is that right "dban-1.0.7_i386.iso" is the file name. Do I have to do anything to it before it will run properly?

Did you burn the iso to cd as a bootable **image**?  won't start if you burned it as data

EDIT/ADD:

Another way to wipe the hard disk is to boot from the ubuntu live cd and run this in a terminal:
> 
sudo dd if=/dev/zero of=/dev/sda conv=notrunc

make sure you get the right drive if you have more than one

---

### Post by paul382 on 2008-07-21
Hi,

For erasing your hard drive via windows XP cd. Boot your partiton using windows XP cd or use 98 bootable cd so that you can go through command prompt. At command prompt use command fdisk and delete all partition and create new partition. Now use windows XP bootable cd and install windows XP operating system. If you still face problem you can use [drive wipe]("http://www.drive-wipe.com") bootable CD to erase your hard  drive completely because it detect that drive which is not able to access.

---

