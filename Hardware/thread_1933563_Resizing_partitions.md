---
title: "Resizing partitions"
date: 2012-02-29
forum: Hardware
---

### Post by Lateralus138 on 2012-02-29
Sorry if this isn't in the right place, but I wasn't sure where to put it...

I have a few partitions and main two are for a Windows installation and the other is for Ubuntu. My Windows partition is running out of disk space and I'm not really wanting to remove anything there as I actually use most of it. My Windows partition has little more than 10gbs, but my Ubuntu partition has well over 90 extra gbs and I was wondering if there was anyway of resizing the Ubuntu partition and changing the new partition for ntfs storage without losing anything or having to reinstall any OSs? I'm old school when it comes to partitions as I learned a long time ago and I am a little familiar with gparted, but I wasn't sure if there are any new ways. 

I'd appreciate any help.

---

### Post by ahallubuntu on 2012-02-29
Gparted is reliable and is probably the way to go, but you will need to do the resizing with your live CD - can't resize the Ubuntu partitions while they are booted.  Depending on your partition scheme, resizing with Gparted could be time consuming.  You could wind up having to wait while a lot of data is copied.  (Growing a partition using free space is very quick though.)

After you resize a Windows partition, expect an automatic chkdsk to be run the next time you boot Windows - that's normal.

Whatever you do, HAVE BACKUPS before resizing partitions; even though Gparted is reliable, things can happen and if you have an error in the middle or resizing, the data in your partitions might be toast.

FYI, I have done some of this with the aid of imaging.  Basically, I copy partitions to a backup disk, resize my original disk partitions by deleting them/re-arranging them (which is pretty quick), then copy them back.  This has the benefit of making a backup copy in the process (image backups).  Copying partitions can be time consuming too, though.

I use True Image, a program from Acronis, for making images of partitions (basically, into big image files).  It's not a free program unless you happen to be a Western Digital drive owner, then it will work with that drive from WD's site.  Maybe the same for a Seagate drive, not sure lately.  To me it's software worth buying.  There are free options like partimage (which doesn't support ext4 last I checked) or just the .) brute-force approach with dd, which is time consuming and copies everything even free space but can work if you know what you're doing.

---

### Post by oldfred on 2012-02-29
You have to shrink the Linux partition and then you usually have to move it so the unallocated is next to the NTFS partition. 

While 10GB is real small for NTFS and NTFS works best if you have 30% free space in the partition another choice is to shrink the Linux partition and make a shared NTFS data partition for any data you want in both Windows and Ubuntu. You may be able to move enough data to leave room in the two system partitions. I usually suggest smaller system partitions and separate shared, data or /home partitions to keep system partition smaller and more efficent.

---

### Post by Lateralus138 on 2012-02-29
> **oldfred said:**
> ...shrink the Linux partition and make a shared NTFS data partition...
This is what I was getting at, but wasn't sure what direction I should go as I am more familiar with Windows than Linux....

I know most of the other things you guys are telling me, but thank you both for your great help.

---

### Post by oldfred on 2012-02-29
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


Shared NTFS partition - You can also use links
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Lateralus138 on 2012-02-29
Thank you very much oldfred.

---

