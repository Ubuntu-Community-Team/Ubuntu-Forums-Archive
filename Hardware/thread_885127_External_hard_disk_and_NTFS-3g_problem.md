---
title: "External hard disk and NTFS-3g problem"
date: 2008-08-09
forum: Hardware
---

### Post by gaelfx on 2008-08-09
I'm using utorrent to download something, and it forces a re-check of the data, only it can't seem to get past a certain point (gives Error: Not Ready), so it' possible the problem is with Wine, however, when I check the syslog, it gives this output:

```
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: Run lists overlap. Cannot merge: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336151552: 131072 <> 65536: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: Run lists overlap. Cannot merge: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336217088: 65536 <> -1: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336217088: 4096 <> -1: Input/output error
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336217088: 4096 <> -1: Input/output error
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: Run lists overlap. Cannot merge: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336151552: 131072 <> 65536: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: Run lists overlap. Cannot merge: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336217088: 65536 <> -1: Numerical result out of range
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336217088: 4096 <> -1: Input/output error
Aug 10 06:45:43 gaelfx-laptop ntfs-3g[6980]: ntfs_attr_pread error reading '/Movies/Matrix_Ultimate_Collection/THE_MATRIX_ROOTS_UNCOMPRESSED_DVD_DISC8_OF_10/MATRIX_ROOTS.ISO' at offset 6336217088: 4096 <> -1: Input/output error

```

so I suspect the problem is with ntfs-3g. Please help me figure out how to rectify this, and don't recommend that I simply reformat, because that's not an option for me (I use the disk on multiple systems, NTFS is the only format that works easily with any given Windows machine).

---

### Post by szaka on 2008-08-10
Make sure you use the latest ntfs-3g 1.2712 version, then run 'chkdsk /f drive:' on Windows, and rebboot Windows twice then boot Linux.

---

### Post by kadakas on 2008-12-22
I have the exact same error message with utorrent. Only I use ext3.

---

### Post by gaelfx on 2008-12-23
Well, it's surprising that you have that error now, because I no longer have it. A few things I've done since the problem first occurred:

Upgraded to 8.10
Started using Wine repos to get the latest version of Wine
Unplugged other USB devices

If you are still using 8.04, I highly suggest an upgrade, Intrepid has done wonders for my computer.

Cheers

---

### Post by kadakas on 2008-12-24
I think its a problem with my hard disk. When utorrent is doing its check the percent gauge just stays at 69.7% for a while and after that the error is shown.

I did a tail -f /var/log/kern.log at the same time and the following errors were displayed after the percent gauge got stuck:

```
Dec 23 01:33:59 L2 kernel: [29571.571875] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Dec 23 01:33:59 L2 kernel: [29571.571891] ata3.00: BMDMA stat 0x24
Dec 23 01:33:59 L2 kernel: [29571.571904] ata3.00: cmd 25/00:08:11:30:9e/00:00:12:00:00/e0 tag 0 dma 4096 in
Dec 23 01:33:59 L2 kernel: [29571.571907]          res 51/40:08:11:30:9e/40:00:12:00:00/e0 Emask 0x9 (media error)
Dec 23 01:33:59 L2 kernel: [29571.571916] ata3.00: status: { DRDY ERR }
Dec 23 01:33:59 L2 kernel: [29571.571922] ata3.00: error: { UNC }
Dec 23 01:33:59 L2 kernel: [29571.596473] ata3.00: configured for UDMA/33
Dec 23 01:33:59 L2 kernel: [29571.596508] ata3: EH complete
```

Multiple of these blocks were shown during the gauge being stuck. Shortly after utorrent displayed "Error: Not ready" and the error messages in kern.log also stopped.

Is my hard drive broken? I just got it brand new over 1 month ago :(

---

### Post by mxxx on 2009-03-10
i've also had this problem, and had a few variations on it. 


originally had it on Hardy, now using Ibex and still getting it.  I have an HFS+ drive hooked up via FireWire, which gives me the error on torrents larger than about 5gb.  I've also had the same problem with an NTFS disk. 

If I move the torrent data over to an EXT3 drive (internal), it goes fine, but someone posted on the uTorrent forum a while back that this also gave him problems. 


so it's hard to figure out, unfortunately.  but upgrading to Ibex gave me no luck.

---

### Post by jackobean on 2009-03-17
> **mxxx said:**
> i've also had this problem, and had a few variations on it. 


originally had it on Hardy, now using Ibex and still getting it.  I have an HFS+ drive hooked up via FireWire, which gives me the error on torrents larger than about 5gb.  I've also had the same problem with an NTFS disk. 

If I move the torrent data over to an EXT3 drive (internal), it goes fine, but someone posted on the uTorrent forum a while back that this also gave him problems. 


so it's hard to figure out, unfortunately.  but upgrading to Ibex gave me no luck.

Just out of interest, do you have journaling turned on for the HFS+ drive in OSX? I've been having issues with Hannah's mac stuffing the partition table on our external HD for Ubuntu/MacDrive, and I suspect it has something to do with journaling. 

I'm wondering weather it might be a good idea to format the drive as ext3, and find a darwin port or something to read/write on OSX?

---

### Post by mxxx on 2009-03-24
journaling's off. it'd probably be a good idea to swap it over to EXT3, but it's an external drive that's primarily for torrents, secondarily for sharing and grabbing things off other people.  not many people can do anything with EXT3.

---

### Post by stchman on 2009-03-24
The OP should use either Transmission(default), Azureus(Synaptic), or K9Copy(Synaptic).

Using uTorrent through WINE is probably not the best way.

I am still amazed that people install Linux to use Windows applications then complain when they don't work perfectly!!!!

There are so many FOSS programs that do the same if not better than their Windows counterparts.

You know K9Copy does not work worth a darn in Vista, I wonder why?

---

### Post by mxxx on 2009-04-05
of course.  it's just unfortunate that uTorrent remains the best torrent software available today, and apart from that single problem works perfectly under wine.

---

### Post by retaylor on 2009-12-28
My own experiences in this differ slightly, but i'm also a bit of a newbie but i've been using xubuntu for ages.

I'm using a PC from the dark ages brought back to life by xubuntu 9.10

it's an athlon700 with very little memory and no USB2.0 so i know i'm asking a lot. I bought a portable external 250GB drive only in the last few weeks and have nearly filled it, partly with p2p downloads.

This slows it down considerably and I'm told it may be fragmented, i have read all about this issue but as it's not an ext3 partition (where fragmentation is less of an issue) and it's not USB2 it goes dead slow.

I'm using Transmission and the only teething problem I had before now was when the drive was unmounted. I got an error and have to simply access the drive before starting Transmission (Obviously!!).

Now I get the same (i assume) error as stated by the guy above. 
"Error: Numerical result out of range (filename.avi)"
and it won't start downloading again.

anyone got any suggestions to-
1: get my external drive going a little faster maybe by defrag or at least error checking
2: recover my partly downloaded torrent

help appreciated, cheers

---

