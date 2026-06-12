---
title: "System Performance (in general harddisk performance)"
date: 2011-02-07
forum: Hardware
---

### Post by Cyber1000 on 2011-02-07
[SIZE=2]I was setting up a fileserver on my own some month ago, I think my speed is not slow, but I don't have good comparison (I searched here for "harddisk performance" on this forum). Perhaps you could say whether this are "good" values or not.[/SIZE]
 
[SIZE=2]My hardware configuration (in short):[/SIZE]
[LIST]
[*][SIZE=2]Zotac Mobo with an ATOM D510 [/SIZE]
[*][SIZE=2]8Gb USB-Stick holding /, /boot, /usr (in short the ubuntu itself) and Swap (though swap isn't used quite often even if I run 24/7 for some days)[/SIZE]
[*][SIZE=2]Data Partitions on 2 WD5002ABYS (RAID Disks) chained to a RAID1 (mdadm) array. (both 500 GiB)[/SIZE]
[*][SIZE=2]Data Partitions on 1 WD10EARS (not raided) - (1TiB)[/SIZE]
[*][SIZE=2]all of them use ext4 on lvm[/SIZE]
[*][SIZE=2]2Gig Ram[/SIZE]
[/LIST][SIZE=2]My software configuration:[/SIZE]
[LIST]
[*][SIZE=2]Ubuntu 10.04.1 LTS[/SIZE]
[*][SIZE=2]Headless (no kde or something else, normally just sshing)[/SIZE]
[*][SIZE=2]Programs (ftp-server, samba, nfs-server, ftp-server)[/SIZE]
[/LIST][SIZE=2]My tests (I did them only between partitions in the system, not over network, I assured that there is no load from external access. e.g. ftp-download or something else):[/SIZE]
[LIST]
[*][SIZE=2]hdparm -tT[/SIZE]
[*][SIZE=2]Copying a dataset (between the "normal" disk and the raid) - [SIZE=2]20,6 GiB ([FONT=Calibri][FONT=Verdana]145.056 Files, [FONT=Calibri]51.882 Directories)[/FONT][/FONT][/FONT][/SIZE]
[/SIZE]
[*][FONT=Calibri][SIZE=2][FONT=Verdana]Testing with dd (32GiB):[/FONT][/SIZE]
[SIZE=2][FONT=Verdana][SIZE=2]time sh -c "dd if=/dev/zero of=<File in Filesystem> bs=4096 count=$((2**20*$2/4096)) && sync" - [/SIZE][/FONT]
[SIZE=2][FONT=Verdana]similar for reading.[/FONT][/SIZE]
[/SIZE][/FONT]
[/LIST]

[SIZE=2][FONT=Verdana]The results:
[LIST]
[*]Normal Drives:
[*]hdparm:
[/LIST][/FONT][/SIZE]
[LIST]
[*]
[LIST]
[*][SIZE=2][FONT=Verdana][SIZE=2]Timing cached reads: 1618 MB in 2.00 seconds = 808.61 MB/sec[/SIZE][/FONT][/SIZE]
[*][SIZE=2][FONT=Verdana][SIZE=2]Timing buffered disk reads: 316 MB in 3.01 seconds = 104.88 MB/sec[/SIZE][/FONT][/SIZE]
[/LIST][SIZE=2][FONT=Verdana]
[*]dd: 702,8Mbit write, 720,2 read[/FONT][/SIZE][SIZE=2][FONT=Verdana]
[*]RAID:
[LIST]
[*]hdparm:
[/LIST][/FONT][/SIZE]
 

[LIST]
[*]
[SIZE=2][FONT=Verdana][SIZE=2]Timing cached reads: 1606 MB in 2.00 seconds = 802.59 MB/sec[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Timing buffered disk reads: 338 MB in 3.00 seconds = 112.61 MB/sec[/SIZE]
[*]dd: 766,5Mbit write, 792 read[/FONT][/SIZE]
[/LIST][SIZE=2][FONT=Verdana]
[*]between both:
[LIST]
[*]copy dataset:
[LIST]
[*][FONT=Calibri][FONT=Calibri][FONT=Verdana][SIZE=2]cp -a: 8,5 mins (345 Mbit/s)[/SIZE][/FONT][/FONT][/FONT]
[*][FONT=Calibri][FONT=Calibri][FONT=Verdana][SIZE=2]rsync -av: 11,5 mins (245Mbit/s) - CPU-load at 120% (Atom D510 is a dual core)[/SIZE][/FONT][/FONT][/FONT]
[/LIST]
[/LIST][/FONT][/SIZE]
[/LIST][LIST=1]
[*][FONT=Calibri][FONT=Calibri][FONT=Verdana][SIZE=2]How do these values look to you? Normal? [/SIZE][/FONT][/FONT][/FONT]
[*][FONT=Calibri][FONT=Calibri][FONT=Verdana][SIZE=2]May the usb-drive lead to problems (it is cold, so I assume not to much read/writes to it, as said my data is on "real" drives)? If you see bottlenecks please tell ...[/SIZE][/FONT][/FONT][/FONT]
[*][FONT=Calibri][FONT=Calibri][FONT=Verdana][SIZE=2]May there be any good performance/benchmarking tools? As said it's a headless server, so I would need one for the commandline. [/SIZE][/FONT][/FONT][/FONT]
[*][FONT=Calibri][FONT=Calibri][FONT=Verdana][SIZE=2]Are there any good comparison sides, where you could check, how a specific harddisk performs on differnet systems (for example a good support forum for a benchmarking tool)[/SIZE][/FONT][/FONT][/FONT]
[/LIST][FONT=Calibri][FONT=Calibri][FONT=Verdana][SIZE=2]Thanks for your patience, (and sorry for the somehow scrambled lists in this post, the editor seems to do this ...)[/SIZE][/FONT][/FONT][/FONT]

---

### Post by Cyber1000 on 2011-02-08
Hi all!
I've found bonnie++, works fine, but the former questions still exists, are these values good ones, please help.
The attached picture shows the performance (the upper one is my "normal" disk, the lower one is my RAID 1)

---

### Post by gordintoronto on 2011-02-08
First of all, don't use a flash drive for swap. The flash drive may suffer premature failure.

Second, copying small files is not a good way to compute disk speed. There is so much overhead in creating folders and directory entries, the data transfer is just noise. Far better to get a 4 GB .MKV and time that.

Third, if it seems slow, it's because your CPU is slow.

---

### Post by Cyber1000 on 2011-02-08
Hi!
Thanks for the fast answer. But I want improve things, performance doesn't look bad in my eyes, but I wanted to hear some other thoughts.
 
1) My first thoughts of using an USB-stick for the OS+SWAP were that I may eventually set the harddisks to standby if I'm not at home, cause mobo/cpu/memory/usb need no more than 15-20VA. I know of the problem of flashwear, but I didn't think that it's so important, for now the maximum whats used of RAM is about 500MB (out of 2Gig), the swap wasn't really used by now ... . Perhaps I'll move to SSD, if they are a little bit cheaper.
 
2) I know, I tried a subset of my backup set and there are normally a lot of small files in there. But thanks for pointing it out, yes a bigger file would be more representative to test the speed as it.
ok here it comes: Copying between RAID and normal disk:
8,7Gb in 1:45 mins = 677 Mbit/s which would go into the direction of my "dd" tests.
So I assume the truth lies somewhere between 600-800Mbit/s. Depending on source/destination.
 
3) It doesn't seem slow to me, actually in real life my gigabit-network wouldn't be really faster. I did some tests, bonnie++ too, but I don't know what I could do with these values ... . Are they good, bad, may I improve my setup (how?) or should I keep my setup.
I know the CPU is not the fastest, but load is at 120% with rsync, (50% with normal copy) so I assume drive, I/O or something else sets the limit.

---

