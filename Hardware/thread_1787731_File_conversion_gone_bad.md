---
title: "File conversion gone bad"
date: 2011-06-21
forum: Hardware
---

### Post by devil103 on 2011-06-21
I just had the strangest experience transforming my data from a Windows Home Server to a Ubuntu Based fileserver.

Situation:
2 HDD, both SATA, both NTFS so I'm faced with the task of converting them to ext4 and not enough storage space to keep two copies of everything 

After some research I decide to create an ext4 partition, fill it up using a Ubuntu live CD (so files never leave the drive, just copied from NTFS partition to ext4 partition), and then using GParted shrink the NTFS partition smaller, add the free space to the ext4 partition and copy some new files in the same way as above. In the end I have to fully ext4 drives.

And then the problem: a lot of my video files now seem corrupt. I can play them all (all types of formats mkv, avi, DVDs) but after a few minutes of playing all programs shut off.

So the seek index of all these files seems corrupted somehow. 
Some further investigations: a typical file is 1.66 GB in Windows NTFS and is now only 1.1 GB in ext4. However this seems normal since even working files are 1.1 GB.

And after some further research only the files come from drive 1 are corrupt, the other files from drive 2 play just fine and they were copied in the same manner.

So to sum up:

-only video files from drive 1 are affected (music and photos are fine)
-file sizes seem correct, approximately the same as the files from drive 2

Questions: What could have caused this kind of behaviour? Both drive were exactly the same and treated the same.

Secondly: is there a way to repair the mkv files? AVI files seem repairable, however all my searches for an mkv repair tool have pointed to project Meteorite (meteorite.sourceforge.net/) which just doesn't work for me (neither on Windows or Linux)

Thanks

---

### Post by Beacon11 on 2011-06-21
Have you run fsck on the partition?

---

### Post by jerrrys on 2011-06-21
is this vista ?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=vista+gparted&sa=Search&cof=FORID:9#911](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=vista+gparted&sa=Search&cof=FORID:9#911)

---

### Post by devil103 on 2011-06-22
I have run an FSCK on both drives to no avail.
It seems I was wrong about it only being from 1 drive.
Video files on both drives have been affected.

I still haven't been able to find a single corrupt photo or mp3 file though. But perhaps a few wrong pixels in an entire JPEG aren't noticeable anyway...

Too bad this file conversion has gone bad. 
To answer your question both drives were without OS. Simply data storage, 2 single partitions formatted as ntfs.

I'm still hoping to restore the files somehow since all data seems to be there?! All files are approximately the correct size.

---

### Post by Beacon11 on 2011-06-23
Oh! Looks like someone else has a relatively similar problem: [http://www.linuxforums.org/forum/hardware-peripherals/179960-video-file-conversion-gone-bad.html](http://www.linuxforums.org/forum/hardware-peripherals/179960-video-file-conversion-gone-bad.html)

---

### Post by devil103 on 2011-06-23
Unfortunatly it seems the problem is not coming from the ext4 conversion; I just found a folder on another NTFS partition which was copied from drive 1 to drive 2 and then to a Windows 7 drive. All three drives connected through SATA and all partitions were NTFS. Files were even copied in the same session and still every file in that folder is corrupt.

I just ran low-level SMART checks on all three drives and they all passed so the problem lies somewhere else.

Unfortunatly this is no longer seems to be a file conversion problem but more of a SATA/NTFS filesystem problem

---

