---
title: "How to read a DOS hard drive in Ubuntu"
date: 2014-10-10
forum: Hardware
---

### Post by Michael_McKenney on 2014-10-10
My brother's computer is ancient.  He is running DOS 6.22 and PFS First Choice for his business.  Last week, he ran out of hard drive directory creation in the structure.   No CD/DVD drives.   Hard drives are ATA.   No USB connections.   Ancient.  

Last night, we went to Best Buy to get a laptop with Windows 8 and Office.  I found software to convert PFS First Choice to Office.  How do I get the files off.  It has a second hard drive I use as a back drive.   One of my Ubuntu boxes has ATA connections.   How do I get Ubuntu to read a DOS formatted drive?  We are talking 48 MB of data.  I backed up to a Travan tape drive.   No drivers or way to get it to work in my other workstations.  

I am backing up to tape. I have not tried a restore from a Travan in years.   I hate moving hard drives to other computers unless I have to.  Especially production computer hard drives.   I figured Ubuntu might be more friendly than Windows 7 to the drive.  I know Windows 7 will mount and change the partition slightly.  I can't lost the data.  It is his business records for 10+ years.  


I considered several options
1.) PCI USB 2 card and Panasonic USB DOS drives to bring the data over.  I am trying this tonight.   
2.) Move the hard drive into my Ubuntu box and copy the data over to a thumb drive. 

Will Ubuntu do anything to change the DOS partition.  I just want to access it to copy off the data.

---

### Post by mikewhatever on 2014-10-10
Not really sure what the fuss is about. Both Ubuntu and Windows can read FAT file system, and, I am sure your brother has a backup, given the files are so very important.

---

### Post by Michael_McKenney on 2014-10-10
The last time the hard drive got corrupted. It cost $2000+ at Ontrack to recover his business files.  Read FAT is not the problem.  Windows will change the drive slightly to mount it.   I want to make sure Ubuntu does not.

---

### Post by sudodus on 2014-10-10
You can mount the partition on your brother's hard disk drive read-only to be on the safe side:

```
man mount
```

```
mount -r /dev/sdxy /mnt
```

where **x** is the device number and **y** is the partition number. If no partition, mount the device directly:

```
mount -r /dev/sdx /mnt
```

-o-

You can also clone your brother's hard disk drive with ***ddrescue*** to another drive of at least the same size, and then use the cloned copy to read the files. ***Warning***: You must be 100% sure what is the source and target in the ddrescue operation. So double check and triple check to avoid overwriting the valuable data.

---

### Post by Michael_McKenney on 2014-10-10
Cloning sounds risky.  I need 0% risk. Mount it and copy the data off to a thumb drive. It is 48MB of data. Copy to his new laptop.  Run the conversion program to convert the PFS files to Word.  Test them to verify the conversion worked.  I want to keep the main drive in tact to reboot DOS.   

So I can mount as read only.  Sounds like a good plan.  It is DOS with only drive C: on the drive.  Drive D: is on second hard drive.  So I was going to copy everything to D: and move it into my Ubuntu box.  Keeping C: in tact.

---

### Post by sudodus on 2014-10-10
Yes, try acoording to that plan. I suppose you intend to boot his computer from a live linux CD/DVD/USB drive. If the computer is very old, you may have problems to boot it from a modern Ubuntu desktop iso file. Maybe it works better with ***Wary Puppy*** or some other linux distro designed to work with old hardware.

Good luck :-)

---

### Post by kurt18947 on 2014-10-10
Not a pro here so take it for what it's worth.  If your brother would be that far up the creek in case of a problem, would it be worthwhile to buy another IDE drive, replace the existing D: drive with this one, do a copy *.* type command to the new hard drive and work with the files there? That seems like a low risk procedure. I just bought an 80 GB. 'reconditioned' IDE hard drive at MicroCenter for $12.

---

### Post by Michael_McKenney on 2014-10-10
C: is the main drive.  D: is a backup I put in as a spare to protect his data.  Finding IDE and ATA stuff can be hard.  I was going to Microcenter tonight to see what they had in hardware.   The board was my very old Tyan Tomcat IVD.  It actually has a pair of Intel Pentium 233 CPUs Socket 7.  I built it for him years ago.  I still remember my DOS commands.  It has a 3.5" floppy drive.  I have a set of floppies with the OS and tape software on it.   I hate working with old hardware and this is ancient.

---

### Post by Mark Phelps on 2014-10-10
>  I was going to Microcenter tonight to see what they had in hardware.

What you're calling an "ATA" drive is probably an old PATA drive.  You can tell because it has two rows of small pins in the back of the drive.

The local MicroCenter has not carried new PATA drives in a long time.  Best you probably will be able to find is "reconditioned" used PATA drives.  And, depending on the age of the BIOS on the PC, it might not be able to handle anything larger than a 120GB drive.  I had an old P4 latop whose hard drive failed and I tried to use a new 240GB drive -- and the BIOS couldn't read it.  I had to settle with one of their reconditioned 80GB drives.

As to copying things over, if you don't already have one, consider getting one of the external SATA/IDE adapters from MicoCenter.  You connect the drive to that, and then connect the adapter to a USB port on the PC, and you can then transfer stuff from the PC hard drive to the external hard drive.

I would also suggest, if you're going this route, to install the FREE version of Macrium Reflect on the Windows PC.  Using that, you could then "clone" the old drive partitions to the new drive -- which will be faster and easier than copying files and folders.

---

### Post by sudodus on 2014-10-10
> **Mark Phelps said:**
> ...
As to copying things over, if you don't already have one, consider getting one of the ***external SATA/IDE adapters*** from MicoCenter.  You connect the drive to that, and then connect the adapter to a USB port on the PC, and you can then transfer stuff from the PC hard drive to the external hard drive.
...

+1

Sometimes called ***USB2.0 to IDE & SATA cable***

---

### Post by Michael_McKenney on 2014-10-10
I can put on the ATA cable next to the box.  I usually just touch the side of the drive to the chassis to keep a ground.  USB2.0 is slow for transferring small files.  My concern was FAT to Ubuntu.

---

### Post by sudodus on 2014-10-10
Linux can read FAT file systems, I think since the very beginning. Most USB pendrives are delivered with FAT32, and they can be read by Ubuntu. See ```
man mount
``` where you find a separate section about fat as well as about vfat.

---

### Post by Michael_McKenney on 2014-10-13
I copied the data from C:\ to D:\ and backed up twice to tape.  I removed the D: drive and mounted it in Ubuntu.  It read the drive and copied everything to the thumb drive.  It is now in a directory on his new laptop waiting for the converstion software.   Thank you for all your help.

---

### Post by sudodus on 2014-10-13
You are welcome. I'm that you could solve the problem :KS

---

