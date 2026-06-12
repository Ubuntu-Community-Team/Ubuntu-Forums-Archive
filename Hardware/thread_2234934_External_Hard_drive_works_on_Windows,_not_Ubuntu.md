---
title: "External Hard drive works on Windows, not Ubuntu"
date: 2014-07-17
forum: Hardware
---

### Post by matthew31 on 2014-07-17
I have a laptop hard drive in a Mediasonic ProBox H21-SU3 enclosure. I was going to format it to ext4 since I only really use this drive on my Linux computers. When I try to format it it fails every time. I even tried to recreate the partition table and I tried both DOS and GPT with Gparted.

I went back to my Windows computer, and formatted the drive as NTFS and FAT32 and both work fine on Windows, but when I come back to Ubuntu the drive refuses to mount.

What could be causing this? I can't find anything about this chip set not being supported by my computer. My motherboard is an ASUS P8Z77-I DELUXE.

---

### Post by yancek on 2014-07-17
> When I try to format it it fails every time

So what happens when you try to format and how are you trying to format?  What command?  Are you using GParted?

Linux systems like Ubuntu are fully capable of mounting, reading and writing to vfat and ntfs.  Exactly how are you trying to mount these partitions?

---

### Post by matthew31 on 2014-07-17
It doesn't finish. it just halts. As for mounting it pops up with some error saying the device is not ready when I click on it. I'm able to delete the partitions in Gparted just fine, but when I create a partition or try to mount a NTFS or FAT32 filesystem on this drive it fails. Other drives work just fine.

---

### Post by sp40140 on 2014-07-18
I have had this issue a while back with SD Card. The reason was SD card was bad. Windows was able to format it to either fat for ntfs, but when I tried to fill it up or near it's capacity, the files wouldn't copy even in windows. I think windows lets you format bad drives while Linux doesn't (it's a good thing).
So, I suggest you make sure that you don't have issue with your drive. 
I understand that SD card and platter drives are different animals, but the symptoms are same.

---

