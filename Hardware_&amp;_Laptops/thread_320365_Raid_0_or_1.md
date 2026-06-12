---
title: "Raid 0 or 1"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by Ace2016 on 2006-12-17
Hi all

I'm trying to get the fastest possible READ speeds, the write speeds are not as important since this is the / partition and most of the data will only be read from there. I've read that raid0 is the fastest and that raid1 is the same speed as a single disk and stores two coppies of the data on each disk and also reads the exact same data from both disks to make sure its correct. However i want a raid1 but force each disk to read different things, so like if open office is starting, one disk will read one file, the other will read the second, and the first will go read the third file, instead of them both reading the first file, then the second and then the third.

Is this possible? or do i have to stick with raid0

Also if it is posilbe, its faster than raid0 right?

---

### Post by maxamillion on 2006-12-17
It isn't possible.

---

### Post by Ace2016 on 2006-12-17
RAID 1D (Duplexing)

Read Speeds: "Very good. Depending on the software implimentation, up to 100% better.  Simultaenous reads from two controllers.  Butchered as this terminology usage may be, if the software implimentation is good; you can think of it as "Striped Controllers", where while one reads, the other is reading the next sequence according to the size of the read buffer."


So how do i do this in ubuntu?????

I really want this now!!

---

### Post by maxamillion on 2006-12-17
> It isn't possible.

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by Ace2016 on 2006-12-17
> To maximize performance benefits of RAID 1, independent disk controllers are recommended, one for each disk. Some refer to this practice as splitting or duplexing. When reading, both disks can be accessed independently and requested sectors can be split evenly between the disks. For the usual mirror of two discs this would double the transfer rate. The apparent access time of the array would be half that of a single non raid drive. Unlike RAID 0 this would be for all access patterns as all the data is present on all the disks. Read performance can be further improved by adding drives to the mirror. Three disks would give you three times the throughput and an apparent seek time of a third. The only limit is how many disks can be connected to the controller and its maximum transfer speed. Many older IDE RAID 1 cards read from one disk in the pair, so their read performance is that of a single disk. 

Do you mean that its not possible in ubuntu?
_____________________________________________________________________

Disk /dev/hda: 

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        7308    58597087+  fd  Linux raid autodetect
/dev/hda3            7309        9151    14803897+  83  Linux
/dev/hda4            9152       24792   125636332+  83  Linux

 Timing cached reads:   1072 MB in  2.00 seconds = 535.58 MB/sec
 Timing buffered disk reads:  150 MB in  3.04 seconds =  49.34 MB/sec
_____________________________________________________________________

Disk /dev/hdc:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2611    20972826    c  W95 FAT32 (LBA)
/dev/hdc2            2612        9906    58597087+  fd  Linux raid autodetect
/dev/hdc3            9907        9964      465885   82  Linux swap / Solaris

 Timing cached reads:   1076 MB in  2.01 seconds = 536.53 MB/sec
 Timing buffered disk reads:  154 MB in  3.01 seconds =  51.20 MB/sec

_____________________________________________________________________

---

### Post by maxamillion on 2006-12-17
Its a hack job technology that you speak of and you would have to find a software controller to handle scheduling to each platter of each disk to accomplish such a thing and last time I checked ubuntu, nor any linux distro, was able to do this. I assume this to be a proprietary technology that is implemented by someone like IBM on high end storage servers.

If you are able to find such software for linux, please share ... I would love to implement something like this on my servers, but I really don't believe it is at all possible under linux.

---

### Post by gilgongo on 2006-12-17
Would not mdadm let you set up RAID0 on two IDE channels?

---

### Post by Ace2016 on 2006-12-17
I'm not using raid0 because (as far as i know) the data is only stored on one disk, and i want the backup that raid1 offers, i tried raid0 and its not that great. Also if the data is on both disks it would be faster than raid0 since it can read two different files at the same time, but with raid0 the same file is split onto two drives so it wouldn't be as fast since both drives need to be accessed for a single file. e.g if a file from md0 is coppied to /dev/hdc3 and md0 is a raid0 device with hda2 and hdc2, some of the file is being read and written to hdc, so its slow, but if it was raid1, it could in theory be totally read from hda and coppied to hdc, without any of the file being read from hdc. so its faster, hda just reads and hdc just writes. with raid0, hda reads (and only half of the file at that) and hdc has to read the other half and write the whole thing, so its slow. so Raid1 with duplexing is the clear winner :)

FreeBSD can do it, so why can't linux? its free to so can it be ported?

[http://www.onlamp.com/pub/a/bsd/2005/11/10/FreeBSD_Basics.html](http://www.onlamp.com/pub/a/bsd/2005/11/10/FreeBSD_Basics.html)

can g mirrior be used in linux?

---

### Post by gilgongo on 2006-12-17
Oh I see. I would be a lot of fun getting gmirror to work with Ubuntu I think. What about RAID5 on three (or four?) physical disks? That would give you the redundancy if one of your disks went poppo, as well as some read speedup, no?

Having said that, you're probably way more knowledgable than me about this...

---

### Post by Mike'sHardLinux on 2006-12-17
Ace is misunderstanding how RAID works. The Wikipedia does about as good a job explaining RAID as you're going to get anywhere.

RAID 1 is when two drives have the same data....they are mirrored. This is for REDUNDANCY, NOT SPEED. RAID 1 doesn't read 1 file from drive A and another file from drive B. That is NOT how it works. It reads/writes the same data from both drives at the same time, and if one of them croaks, the other [hopefully, but not always] keeps on going, therefore you don't lose data or have downtime.

FreeBSD does NOT do what you are describing. That link is about plain old software RAID 1, which is actually going to be even slower because of processing overhead.

The advantage of RAID1D that is mentioned, is based on using two separate controllers. Supposedly, each controller can seek a different sector. This isn't equivalent to reading different files at the same time, although it's the same idea. The thing is, there'd need to be some software or firmware to tell the controllers to do that and I don't know what controller(s) you can buy to do that. Just setting up RAID 1 on 2 separate controllers on your motherboard will not split the reads of sectors the way described at Wikipedia.

Another thing. That last paragraph in your last post is wrong. In RAID, all drives are either reading or writing at the same time. It's just that simple.  If one drive reads and the other writes, that wouldn't even work. If you write data to only one disk, you can't read it from another disk???

You said your tried RAID0. What kind of RAID0 did you try? Software RAID0? Do you have a RAID controller on your motherboard, or possibly a **real** RAID controller , like on a server?

---

### Post by Ace2016 on 2006-12-17
i tried software raid0

and i was describing raid1 (md0) copying to a partition on one of the disks where md0 is.

so md0 = hda2 + hdc2

file is coppied from md0 to hdc1

something like that

While i was copying stuff while raid0 was in use, as described above, i was unable to even play an mp3 file without it skipping, so i'm not trying raid0 again, i might just stick with raid1 for now :(

---

### Post by Ace2016 on 2006-12-19
[http://www.die.net/doc/linux/man/man4/md.4.html](http://www.die.net/doc/linux/man/man4/md.4.html)

> RAID1 

A RAID1 array is also known as a mirrored set (though mirrors tend to provide reflected images, which RAID1 does not) or a plex. 

Once initialised, each device in a RAID1 array contains exactly the same data. Changes are written to all devices in parallel. Data is read from any one device. The driver attempts to distribute read requests across all devices to maximise performance. 

All devices in a RAID1 array should be the same size. If they are not, then only the amount of space available on the smallest device is used. Any extra space on other devices is wasted.

So shouldn't md0 be faster than the individual disks, and this is the man page of md after all, so what gives, i'm now totally confused

---

