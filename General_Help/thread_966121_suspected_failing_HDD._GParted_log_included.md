---
title: "suspected failing HDD. GParted log included"
date: 2008-11-01
forum: General Help
---

### Post by csc2ya on 2008-11-01
I've currently got a dual boot setup on my laptop with both Windows Vista Ultimate, and also Ubuntu Ultimate Edition (Based on hardy heron ([http://ultimateedition.info](http://ultimateedition.info)))

I currently have Vista installed on the internal drive, and Ubuntu installed on a 116GB partition on my external USB Harddrive. I use the Vista bootloader with an extra entry which starts grub, which then starts the top entry in my grub configuration file after 1 second.

For the last month or so, when booting ubuntu after my laptop has been off for a while, the external drive has had problems spinning up (as in, it hasn't spun up at all). I can usually get round this by pressing escape just before grub starts, selecting recovery mode, and when it gets to 'reading files needed to boot', repeatedly switching the external drive on and off until it spins up.

Once the drive has spun up, it's fine during all subsequent reboots until my laptop has been off for a while (overnight, for example). It also always spins up fine when starting windows, and shows up fine on that.

At the moment this still works. However, i'm concerned that the drive may be failing. I've booted from an Ubuntu 8.04 livcd and run gparted to do a filesystem check. However, i'm not really sure how to interpret the results:

> GParted 0.3.5

Libparted 1.7.1

Check and repair filesystem (ext3) on /dev/sdb2  02:53    ( SUCCES )
     	
calibrate /dev/sdb2  00:00    ( SUCCES )
     	
path: /dev/sdb2
start: 244204065
end: 488392064
size: 244188000 (116.44 GiB)
check filesystem on /dev/sdb2 for errors and (if possible) fix them  02:53    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb2
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

385009 inodes used (5.04%)
2092 non-contiguous inodes (0.5%)
# of inodes with ind/dind/tind blocks: 12022/164/0
2176699 blocks used (7.13%)
0 bad blocks
1 large file

264601 regular files
25577 directories
69 character device files
26 block device files
2 fifos
462 links
94720 symbolic links (92871 fast symbolic links)
5 sockets
--------
385462 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( SUCCES )
     	
resize2fs /dev/sdb2
     	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 30523500 blocks long. Nothing to do!


========================================



Has anyone got any idea whether anything on the gparted results shows any filesystem corruption or anything like that?

P.S.: I did accidently remove the wrong partition from the wrong drive last month when I needed to resize one of my windows partitions (ended up getting totally confused and removed my linux partition). I was able to recover that by running testdisk on the drive though. That may have something to do with it, although i'm unsure.

---

