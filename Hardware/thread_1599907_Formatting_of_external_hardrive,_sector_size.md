---
title: "Formatting of external hardrive, sector size?"
date: 2010-10-18
forum: Hardware
---

### Post by ianc1 on 2010-10-18
Hi everyone, bit of a basic question I fear from a relative newbie.  I’ve just purchased a Western Digital Elements 1TB external hard drive (WDBABV0010BBK) and am probably going to reformat this (currently NTFS) to EXT4.  I cannot tell from Western Digital’s website if this uses the new Advanced Format (4096 byte sectors) or 512 byte sectors.

If I run fdisk will this provide accurate information on the sector size?  Also will parted (I think that’s the formatting command) with the –a and optimal optional really set the formatting up correctly irrespective of Advanced or Normal format or do I need to do anything special.  In the forum I’ve read a lot about drive/partition alignment which I don’t really fully understand.

I’m running 10.10 and do not wish to sacrifice too much on the drives performance by getting the formatting non-optimal.

Thanks

Ian

---

### Post by srs5694 on 2010-10-18
Some utilities might report the information correctly, but don't count on it. To be safe, create partitions that start on 8-sector boundaries. You can do this with recent versions of fdisk by launching it with the -cu option ("sudo fdisk -cu /dev/sdb", say). This actually sets it up for 2048-sector (1 MiB) alignment, but as 2048 is divisible by 8, that should work fine. Alternatively, recent versions of gdisk do the same and use the newer GPT scheme (but the version that Ubuntu delivers is woefully out of date; check the [GPT fdisk downloads page](http://sourceforge.net/projects/gptfdisk/files/) for the latest version).

For more information, see [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the subject. Note that some of the partitioning tools have evolved since then, but I don't know precisely what versions you might be running, so you should definitely check the alignment with fdisk using its sector-alignment mode, or with gdisk (which always uses sector mode).

---

### Post by cascade9 on 2010-10-18
After looking around the WD site, it does look like the new 1TB 2.5'' discs are 'advanced format' drives, so there is a good chance that your WDBABV0010BBK is an advanced format drive. 

Without popping the cover off, I cant know for sure what HDD is instaled in there though.

---

### Post by ianc1 on 2010-10-19
Thanks srs5694 a nice article you wrote there which has certainly helped my understanding.  Thanks also cascade9.  I don't wish to open up the device to check but the device was originally released early 2009 which as I far as I know is pre-Advanced Formatting, however my model was purchased this week with now way of telling when it was manufactured.

I suspect my best bet is to send the serial no to Western Digital and ask.

If I use gparted or Ubuntu's Disk Utility to reformat the partition am I correct in thinking that I am not moving the partition boundary (disk only has 1 partition) but am simply reformatting the current partition?

Thanks

---

### Post by srs5694 on 2010-10-19
There's next to no harm in playing it safe and formatting any disk that even just might possibly maybe in a blue moon be an Advanced Format disk as if it were definitely one. If you use modern OSes, the only down side to this is that you'll lose a tiny bit of disk space -- perhaps as little as 512 bytes, depending on how you set up your partitions. If you boot very old OSes, such as DOS, there might be more serious consequences, since such OSes sometimes assume cylinder alignment. AFAIK, such OSes can't cope with a disk as large as 1 TB, though.

---

### Post by cascade9 on 2010-10-20
> **ianc1 said:**
> Thanks srs5694 a nice article you wrote there which has certainly helped my understanding.  Thanks also cascade9.  I don't wish to open up the device to check but the device was originally released early 2009 which as I far as I know is pre-Advanced Formatting, however my model was purchased this week with now way of telling when it was manufactured.

I suspect my best bet is to send the serial no to Western Digital and ask.

WD (and everybody else for that matter) has been known to change the internal HDD as stock/production allows (or even demands). Since it doesnt look like WD is making 1TB 2.5'' drives that arent Advanced Format drives anymore, even if you dont have an advanced format drive, sooner or later all the WDBABV0010BBK drives will be. 

There would probably be at least a hint in the full model name. (WDBABV0010BBK-EESN, WDBABV0010BBK-PESN, etc).

---

### Post by ianc1 on 2010-10-20
The box had perhaps a more meaningful product number WDBAAU0010HBK-UESN.  Assuming the UESN bit may have been relevant I went to the WD web site but couldn't find any details only this.  So I used the WD web site to fire off a query to them.  I simply asked about the supplied formatting, I hope I don't get a we don't support Linux type response.

Cascade9 do you know what the UESN bit is?

---

### Post by cascade9 on 2010-10-20
"UESN" will just be a revision. Gawds only know whats been changed between the revisions (could be the drive, the USB->SATA interface, casing, etc). 

Sorry that I cant know for sure what drive is in there. :(

---

### Post by srs5694 on 2010-10-21
I'd like to reiterate what I wrote before: Aside from satisfying your curiosity, you don't really need to know whether the disk uses 512-byte or 4096-byte physical sectors. If you partition it as if it used 4096-byte sectors, it'll be fine. If it uses 512-byte sectors, the only thing you'll lose is a very small amount of disk space.

---

### Post by ianc1 on 2010-10-21
Sorry srs5694, I did appreciate the point my interest remained more out of curiosity as to how it was supplied ie was it 4096 or 512 bytes in its original NTFS format.  I know that its now 512 bytes in EXT4 format as I reformatted it.

WD did not provide any info in reply to my query other than its not possible to say what drive is in what device, which seems odd to me given I quoted its serial number but nevermind.

---

