---
title: "More than 500 bad sectors in HD"
date: 2012-05-23
forum: Hardware
---

### Post by ynkobs on 2012-05-23
I can't access any of my 3 OS (win7, ubuntu 12.04, and slackware 13.37), all 64 bits, on my Dell laptop.

Grub give me errors for any attempt to start any OS.

And the SMART Data option on the Disk Utility of Ubuntu LiveCD is saying that there are 539 bad sectors.

I can't access my Ubuntu ext4 partition (I can access the others).

I searched over the internet, and I could not find anything good for my problem.

There's a way to access the ext4 "lost" partition?

My main question is: this amount of bad sectors means that my HD is down? (I have to backup accessible data and buy a new HD?)

Thanks.

---

### Post by jjiggens on 2012-05-23
I recently had a failure as well, although i had recent backups their were a few files that were not. 

I used an app called HDD regenerator which repaired the bad sectors, it took 12 hours but after it was done i was able to mount the drive via a usb enclosure and copy off what i needed.

with that amount of bad sectors hdd regenerator may not work for you however testdisk and photorec may work great to at least recover what you can in your case. test disk and photorec are extreme life savers and i have used them many times in my profession to recover data for customers.

---

### Post by ynkobs on 2012-05-23
> **jjiggens said:**
> I recently had a failure as well, although i had recent backups their were a few files that were not. 

I used an app called HDD regenerator which repaired the bad sectors, it took 12 hours but after it was done i was able to mount the drive via a usb enclosure and copy off what i needed.

with that amount of bad sectors hdd regenerator may not work for you however testdisk and photorec may work great to at least recover what you can in your case. test disk and photorec are extreme life savers and i have used them many times in my profession to recover data for customers.

Thanks for the reply. I'll see what I can do.

---

### Post by ynkobs on 2012-05-23
> **ynkobs said:**
> Thanks for the reply. I'll see what I can do.

Look at this screenshot:

[http://img267.imageshack.us/img267/8051/screenshot1yl.png](http://img267.imageshack.us/img267/8051/screenshot1yl.png)

The 30 GB and the 16 GB partition should be inside the extended partition (241 GB), they simply "jumped" out of there.

EDIT: The 30 GB partition was ext4 (where my Ubuntu 12.04 was installed), and the 16 GB was FAT32. And now they are "Unknown" type. I tried to list the files inside the 30 GB partition using testdisk, but I got an error saying that the filesystem must be corrupted.

---

### Post by ahallubuntu on 2012-05-23
Don't expect bad sectors to be "repaired."  Instead, the files that contain those bad sectors may be rendered readable in the filesystem but may still be corrupt, which may help you recover all the other files but not the files that were corrupted.

Bad sectors can either be "soft" errors on the drive which can sometimes be cleared by writing to them, but often they are physical surface failures on the hard drive platters.  Sometimes the drive's firmware can detect that a sector has failed and mark it "bad/do not use" and replace it with a spare sector.  This is called a "reallocated sector."  You can see how many reallocated sectors S.M.A.R.T. reports for a given drive.  An increasing number of reallocated sectors may not be an immediate catastrophe but it's a warning that the drive may be about to fail.  A drive has a finite number of spare sectors, and once the drive runs out of spares, there are no more sectors to "reallocate" bad sectors to - and the drive is junk.

---

### Post by ynkobs on 2012-05-23
> **ahallubuntu said:**
> Don't expect bad sectors to be "repaired."  Instead, the files that contain those bad sectors may be rendered readable in the filesystem but may still be corrupt, which may help you recover all the other files but not the files that were corrupted.

Bad sectors can either be "soft" errors on the drive which can sometimes be cleared by writing to them, but often they are physical surface failures on the hard drive platters.  Sometimes the drive's firmware can detect that a sector has failed and mark it "bad/do not use" and replace it with a spare sector.  This is called a "reallocated sector."  You can see how many reallocated sectors S.M.A.R.T. reports for a given drive.  An increasing number of reallocated sectors may not be an immediate catastrophe but it's a warning that the drive may be about to fail.  A drive has a finite number of spare sectors, and once the drive runs out of spares, there are no more sectors to "reallocate" bad sectors to - and the drive is junk.

This should help you to understand my hard drive conditions:

--

[http://img195.imageshack.us/img195/2918/screenshot2cr.png](http://img195.imageshack.us/img195/2918/screenshot2cr.png)

[http://img208.imageshack.us/img208/6213/screenshot3fo.png](http://img208.imageshack.us/img208/6213/screenshot3fo.png)

[http://img823.imageshack.us/img823/9117/screenshot4ah.png](http://img823.imageshack.us/img823/9117/screenshot4ah.png)

[http://img403.imageshack.us/img403/4439/screenshot5yh.png](http://img403.imageshack.us/img403/4439/screenshot5yh.png)

[http://img152.imageshack.us/img152/3615/screenshot6ov.png](http://img152.imageshack.us/img152/3615/screenshot6ov.png)

--

There's a known way to recover my files in the 30 GB "Unknown" partition?

Thanks.

---

### Post by ahallubuntu on 2012-05-24
You actually have only 11 "bad sectors."  Those are the "pending sectors."  The "reallocated sectors" are the ones already replaced successfully by the drive's firmware with spare sectors.

Those 11 sectors are still in files probably and those files are now corrupt.  (And your hard drive is certainly failing and should be replaced as soon as you recover the files you can.)  But if you're lucky, most of your files may be OK.

I have not used any file recovery tools in Linux, actually, but you can try these:

[http://www.linuxlinks.com/article/20100226122928107/DataRecovery.html](http://www.linuxlinks.com/article/20100226122928107/DataRecovery.html)

---

### Post by ynkobs on 2012-05-24
> **ahallubuntu said:**
> You actually have only 11 "bad sectors."  Those are the "pending sectors."  The "reallocated sectors" are the ones already replaced successfully by the drive's firmware with spare sectors.

Those 11 sectors are still in files probably and those files are now corrupt.  (And your hard drive is certainly failing and should be replaced as soon as you recover the files you can.)  But if you're lucky, most of your files may be OK.

I have not used any file recovery tools in Linux, actually, but you can try these:

[http://www.linuxlinks.com/article/20100226122928107/DataRecovery.html](http://www.linuxlinks.com/article/20100226122928107/DataRecovery.html)

Well, I think there's a big problem here: I need to recover a file from a "Unknown" partition.
I tried testdisk, but it could not get my partition as ext4. Any attempt to mount that partition failed.
I really think that the corrupted sectors are in the beggining of that "Unknown" partition, and it would very hard to recover that files.

Thanks for the replies, but I can handle here without that files. Unfortunately, I don't have sufficient  time to find a fast way to recover that files. I'm going to format my entire hard drive, and then buy a new one.

I appreciate the help. Thanks.

---

### Post by jjiggens on 2012-05-24
Use testdisk to fix the partition table, then hdd regenerator to fix those bad sectors if you can. then i suggest using ghost 4 linux or just copying your data off as fast as you can and retire that drive.

---

