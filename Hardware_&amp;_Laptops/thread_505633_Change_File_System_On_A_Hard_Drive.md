---
title: "Change File System On A Hard Drive"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by ReverendJ1 on 2007-07-20
I have a second hard drive on my computer where I store all my movies, pictures and mp3s. (If my car stereo had support for ogg I would probably convert them all, but thats a different story) Anywho, the hard drive is using NTFS, because I am a Windows convert. It seems to me that the NTFS drivers I have make accessing the hard drive go a little slower than my main native ext3 drive (especially noticeable when backing up movies to XVid) so I would like to convert it to ext3. I have read that there are kernel level ext3 drivers for Windows, which makes me feel a little better about this (I am dual-booting, but have only used Windows a couple times in the past 5 months I have been Ubuntu). 
I was planning on using GParted to resize the empty space, then convert it to ext3 and copy as much of my data as possible to the ext3 partition and repeat this process until the drive is fully converted to ext3. Is this the easiest way to do this without losing data? Has anyone else tried this before? Does anyone see any problems I may run in to?

---

### Post by kngunn on 2007-07-20
Yes, there is a driver available for Windows that will mount an EXT2/3 filesystem, but I have no experience with it.  Otherwise, your process sounds reasonable to me, though terribly time-consuming.  There are also plenty of places for an "oops" that would cause data loss.

If possible, borrow another external drive, copy your files over, reformat the first drive, and then copy them back.  Actually, if the external drive is the only copy of your files you should probably buy another one as a backup anyway.  A drive failure is sad sad thing...

MacMall has some really cheap drives from Fantom that I use for backups (or as a primary drive for an ancient Powerbook I have at home with a dead internal drive).  You should be able to find them elsewhere as well.

---

### Post by ReverendJ1 on 2007-07-20
Unfortunately the hard drive is too big to do a nice clean backup (750 GB, probably ~400 GB used). I know that that would be the best way to do it, I just don't have the resources available for a backup hard drive of that magnitude. I do however have a 40GB external drive, but I don't think that would help much. I have most everything backed up on DVDs scattered throughout my house in case of an emergency, except the movies, but I have the originals, so I would only be out time if something happened to them. I just don't want to have to sit there for several hours and a stack of 100 DVDs to do it the wipe it all out restore from backups thing. :-)
I too know how much it sucks to get hard drive failures, as I have had a couple. Which is why I back up my most important stuff from time to time to DVDs.

---

### Post by gali98 on 2007-07-20
I would suggest defragmenting a couple of times before resizing your partition. I think it's NFTS that you need to defragment. (?) just a suggestion.

---

### Post by ReverendJ1 on 2007-07-21
Yeah, I forgot to mention that as one of my steps. I was planning on booting into Windows and defragmenting, because I know when I set up the dual-boot it was recommended to do. BTW, here is the kernel mode driver I plan on using for Windows to access my ext3 drive [http://www.fs-driver.org/]("http://www.fs-driver.org/") in case any one else cares.

---

### Post by ReverendJ1 on 2007-07-26
Well apparently this didn't end up as smoothly as I had hoped. Now I'm in a little bit of trouble. I used GParted to make the free space on my drive ext3 and moved the data over. Then, when I deleted the NTFS partition and resized the ext3 partition to fill the whole disk, it merely moved the partition to the front of the disk (after 16 hours!). I thought, oh, no biggy, that must just be how GParted works or something. So I booted up the GParted live CD again and tried to grow the partition to fill the disk. After about 45 minutes to an hour Gparted looked like it finished. It was at the screen where it just shows the shutdown button, the screenshot button, etc. So, I restarted it and checked in Ubuntu. The partition was still the same size! I tried growing it a couple more times. If I did it from Ubuntu (this is my second, non-mounted drive) it would just quit after so long of trying to grow and not tell me anything. I tried using QTParted to see if it would tell me anything. That won't even let me grow it, it says it has unsupported flags or something similar. So then I tried rebooting into Windows and using Partition Magic. That says it is a bad filesystem. Grrr.
Now I rebooted back into Ubuntu and thought, oh well, I will just have to live with my drive being two partitions. Not a big deal. So then I decided to look on the drive and check it out, but one of my folders is gone. Sort of. It was replaced with an icon with a lock emblem and a red x emblem. The size of the file is 0. When I look at the properties of the drive, it shows the right amount of used disk space, so I am a little confused there, but it gives me hope.
My next idea was to run fsck so I did this:
```
fsck -a -t ext3 /dev/hdb2
```
but it just says it is good without actually scanning it. Does anyone know how can I repair my drive?

---

### Post by ReverendJ1 on 2007-07-26
I just thought I would clarify. My drive is working fine, except the one corrupted folder. I have opened documents from the rest of the drive fine, but don't dare save anything to it until I get this whole thing figured out. Was I using the right command for fsck to check and repair a file system?

---

