---
title: "change NTFS partition size"
date: 2008-06-05
forum: Hardware
---

### Post by Kalidane on 2008-06-05
Hi y´all

I have a 500G Seagate (Freeagent) USB drive that I want to use as media storage.  Prob is I´ve formatted NTFS and loaded 120G of stuff on it.  Is there any way to reduce the NTFS partition size so I can create a FAT32 partition?  I´ve nowhere else to move the media to or I´d just zap the thing and start fresh.

Edit:  No longer have windows to boot to if relevant

---

### Post by prshah on 2008-06-05
> **Kalidane said:**
> Prob is I´ve formatted NTFS and loaded 120G of stuff on it.  Is there any way to reduce the NTFS partition size so I can create a FAT32 partition?  

What version of ubuntu are you using? From 7.10 onwards, ntfs r/w support is available out of the box. So no need to create a fat32 partition.

If you still want to, though, connect your usb storage to the computer, unmount it's volumes and use gparted to resize (shrink) the ntfs partition.

For more instructions, pls post your ubuntu version.

---

### Post by chrisdugdale on 2008-06-05
Use gparted to work with partitions. If you don't have it you can use System>Administration>Synaptic to add it to your system. It's easy and seems to work every time, no worries mate!

---

### Post by Sef on 2008-06-05
> chrisdugdale  	
Re: change NTFS partition size on USB dev
Use gparted to work with partitions. If you don't have it you can use System>Administration>Synaptic to add it to your system. It's easy and seems to work every time, no worries mate! 

**Back up** your data first.  Reformatting will overwrite your data.  

You can't format a mounted hard drive.  Use the Live CD to resize the partitions.  Applications > Accessories > GParted

---

### Post by Kalidane on 2008-06-05
thanks guys

I´ve only 7.04 at this stage

Gparted won´t let me do anything with that partition

Update manager isn´t saying anything about a new ver available, so I´ll see if I can upgrade the hard way.  Will have a crack at the live CD first as that should be the easier job

---

### Post by prshah on 2008-06-05
> **Kalidane said:**
> thanks guys
I´ve only 7.04 at this stage


OK, You can always download and install ntfs-3g, to gain full ntfs functionality. Or you could upgrade to 7.10. I _think_ 7.04 is supported till October of this year only, so you should be better off upgrading. And if you get the "alternate" cd, you can upgrade via that smoothly.

You can also get a 7.10 "live" cd and use the gparted on that to resize your partition.

Note that the correct upgrade path is 7.04-7.10-8.04 (if you want), ie, you can't "skip" a distribution.

---

### Post by Kalidane on 2008-06-28
Today my update manager did show 7.10 upgrade so I got that done and after solving a few problems that arose it was gpart time.

The lack of need to do so is irrelevant - I´ve made a commitment to the task!  Gpart is currently moving left and resizing with HDD working hard.  We´ll see how safe this is without backing up...  either way the problem will be resolved

Thanks for the answers guys

---

