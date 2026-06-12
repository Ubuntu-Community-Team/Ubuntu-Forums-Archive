---
title: "can u use an advanced format NTFS drive in ubuntu?"
date: 2010-08-31
forum: Hardware
---

### Post by fuzzylogic25 on 2010-08-31
Hi everyone.

I am planning on making a permanent move to Ubuntu 10.04. I just installed Windows 7 and hate it. However I have partitioned a 2TB WD drive which is an advanced format drive as NTFS. So it is one partition 2tb in size of partition NTFS. Now this drive does not hold the operating system, its just used for downloads/data/back up purposes. I have a 300GB 10,000 WD Raptor drive which has Ubuntu and Windows 7 dual boot.

So since I already have so many files on the WD 2TB NTFS Advanced Format drive, I would like to keep it as it is. So my question is, can i use this in ubuntu for regular back ups and constant read/writes even if it is NTFS? I will have software like azureus downloading torrents to it constantly. So alot of disk activity will take place with this drive. Because of that, I am worried if the support is not 100% data corruption might occur

---

### Post by dabl on 2010-08-31
You can't install Linux on a NTFS filesystem, at least not without some extraordinary and unsupported techniques.  It's a bad idea, and if you're really moving to Linux, all that NTFS space has no real future anyway.

---

### Post by dtfinch on 2010-08-31
I've experienced poor performance and high cpu usage backing up a large number of files to an ntfs drive from Linux. Azureus might not run into the same problem though, writing to just a few files, since Wubi seems to run fine hosting an entire root partition in a single file on ntfs. I haven't encountered corruption, but I don't use it often. In the event of a power loss, you might need to either run ntfsfix manually or boot into windows before you can mount the drive again.

[http://www.tuxera.com/community/ntfs-3g-faq/](http://www.tuxera.com/community/ntfs-3g-faq/)
[http://www.tuxera.com/community/release-history/](http://www.tuxera.com/community/release-history/) (Lucid has version 2010.3.6)

---

### Post by fuzzylogic25 on 2010-08-31
well i dont plan on installing ubuntu on the ntfs partition. its just for downloading to and accessing files for personal use. i usually set up my system like this

WD Raptor Drive:
C: NTFS WINDOWS 7
EXT3 UBUNTU 
SWAP

so thats 3 partitions.

and then i have

WD 2TB Advanced Format:
D: NTFS 2TB 

SAMSUNG 1TB:
E: NTFS 1TB


the last two drives are for back ups, downloads, personal data so they are frequently accessed by programs like azureus/vuze, firefox (saving files to there), media players, word etc.

I am wondering if this is ok? I want to keep them as NTFS incase i need to go back to windows to try something. also there is already soo much files on there so i do not want to have to convert or change it. I was also wondering if the fact that one drive is advance format could make a problem?

---

### Post by dtfinch on 2010-08-31
The only issue I'm aware of with advanced format drives is if the partition isn't aligned to 4kb boundaries, it would cause an extra slowdown where it has to read before it writes, but if you formatted the drive in Windows 7 it should be aligned correctly.

---

### Post by fuzzylogic25 on 2010-08-31
where can i get some information on that? i would definitely  like to read into this. thanks!

---

### Post by srs5694 on 2010-08-31
The Advanced Format nature of your drive doesn't really affect the main issue of NTFS support (although if the drive is misaligned there may be performance penalties -- more on that shortly). The main issue for you is the question of NTFS support in Linux. For your stated purpose, you can probably get away with leaving the drive as NTFS in the short term; however, Linux's NTFS support is imperfect. Although the NTFS-3g driver that Linux uses for normal read/write NTFS access seems fairly reliable, it's based on reverse engineering of NTFS data structures, and so may not be 100% reliable. Worse, there are only very limited NTFS maintenance tools in Linux. This means that when (not if, when) the system crashes or you suffer a power outage, you'll be unable to do the routine disk checks that are required of almost any read/write filesystem after such an event. You'll need to boot Windows to do those checks. This will be a minor nuisance if you've still got Windows installed on the system, but the nuisance factor will go up quite a bit if Windows stops working or if you delete it. Furthermore, NTFS doesn't support Linux's file ownership and permissions model, so you'll be limited in what you can do if you ever need to use those features on the disk.

Thus, in the long term you should plan to convert the disk to a Linux-native filesystem. If the disk is less than half full, you could do this by shrinking the NTFS partition, creating a new Linux partition, copying files, deleting the NTFS partition, and resizing the new Linux partition to cover the disk. This will take a while, though, and there's a small risk of losing all your files, particularly if there's a power failure at a critical moment. Alternatively, you could back up to another medium entirely (another disk, DVD-Rs, or whatever), create a new filesystem, and restore.

Now, to the Advanced Format topic: Such drives have 4096-byte physical sectors but present an interface to the OS that gives the illusion of 512-byte sectors. Most modern filesystems also use 4096-byte data structures. This means that, if partitions aren't properly aligned to 4096-byte intervals, writing one of these 4096-byte data structures could involve reading two physical sectors, modifying both of them, and writing them back out. This is slower than just writing a single 4096-byte sector. The result is performance degradation, which can be severe, as shown [in this article I wrote for IBM developerWorks.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) (I've seen numbers for NTFS on Windows that imply a ~3x performance hit, but I don't know how bad it would be under Linux -- it could be either better or worse.) If you set up the disk using Windows 7, it's probably properly aligned at the moment. You should definitely keep this in mind and check the alignment when you make changes.

---

### Post by fuzzylogic25 on 2010-09-01
i have partitioned/formatted the 2tb NTFS Advanced Format WD Drive through Windows 7. It's one of the reasons why I left Win XP.

I am also not worried about ownership and permissions. This really is just for downloads and personal data. No security is required. Once this drive gets full I usually just archive it offline and buy a new one. I guess the new one will be ext3 but right now its hassle for me to change it. I would much rather prefer I just use it as it is. So really what matters to me is, can ubuntu and any applications running on ubuntu perform a large amount of read/writes to that partition without any data corruption? thats all that i really care about.

Also, once these drives become full I just access it through external usb enclosures (so plug a drive into an external enclosure and access it through that). So sometimes I might need to access it through windows (my family members may need to access it too and they use windows), so this is why I wanted to have them as NTFS.

My main partition running ubuntu will obviously be ext3, but i want the data/storage drives to be NTFS for compatibility with windows OS.

Also, i wanted to ask you, what do you think is the best linux for learning unix? I know that I will be working in a unix environment in the near future so having a linux that is closest to unix would be good. I was considering on just installing FreeBSD or something but would prefer to use linux.

---

