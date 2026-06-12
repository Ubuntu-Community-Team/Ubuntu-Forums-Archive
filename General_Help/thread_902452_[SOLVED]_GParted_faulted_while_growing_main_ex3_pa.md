---
title: "[SOLVED] GParted faulted while growing main ex3 partition."
date: 2008-08-27
forum: General Help
---

### Post by nathanscottdaniels on 2008-08-27
I recently deleted (not formated) my Windows XP partition and and last night I was going to grow my Ubuntu partition to fill in the empty space but after about 20 minutes, and error came and said to keep the details for help, which I did (see below).  I plan to make a sacrifice to the computer gods to thank them for not destroying all my data on the ex3 partition, I can still log in and do everything fine.  However, Ubuntu thinks I am using 76.8 GB of my 80 GB HDD when in reality, I am only using around 10 GB.  This is bad because I only have (according to Ubuntu) a few GB of free space left.  Is there any way to fix this without reformatting and reinstalling Ubuntu, which I will NEVER do.

Gparted Details:
```
GParted 0.3.5

Libparted 1.7.1

Grow /dev/hda3 from 9.32 GiB to 70.05 GiB  26:00    ( ERROR )
     	
calibrate /dev/hda3  00:01    ( SUCCES )
     	
path: /dev/hda3
start: 136761345
end: 156296384
size: 19535040 (9.32 GiB)
calculate new size and position of /dev/hda3  00:00    ( SUCCES )
     	
requested start: 9398025
requested end: 156296384
requested size: 146898360 (70.05 GiB)
new start: 9398025
new end: 156296384
new size: 146898360 (70.05 GiB)
check filesystem on /dev/hda3 for errors and (if possible) fix them  02:05    ( SUCCES )
     	
e2fsck -f -y -v /dev/hda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

132292 inodes used (21.62%)
1892 non-contiguous inodes (1.4%)
# of inodes with ind/dind/tind blocks: 8235/464/0
1911938 blocks used (78.30%)
0 bad blocks
1 large file

102750 regular files
13733 directories
69 character device files
26 block device files
2 fifos
366 links
15694 symbolic links (14813 fast symbolic links)
9 sockets
--------
132649 files
e2fsck 1.40.8 (13-Mar-2008)
move partition to the left  00:01    ( SUCCES )
     	
old start: 136761345
old end: 156296384
old size: 19535040 (9.32 GiB)
new start: 9398025
new end: 28933064
new size: 19535040 (9.32 GiB)
move filesystem to the left  18:50    ( SUCCES )
     	
using internal algorithm
copy 19535040 sectors
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:06    ( SUCCES )
     	
32768 of 32768 copied
6.6862 seconds
copy 32768 sectors using a blocksize of 128 sectors  00:07    ( SUCCES )
     	
32768 of 32768 copied
6.50297 seconds
copy 32768 sectors using a blocksize of 256 sectors  00:05    ( SUCCES )
     	
32768 of 32768 copied
5.54869 seconds
copy 32768 sectors using a blocksize of 512 sectors  00:05    ( SUCCES )
     	
32768 of 32768 copied
4.4392 seconds
copy 32768 sectors using a blocksize of 1024 sectors  00:03    ( SUCCES )
     	
32768 of 32768 copied
3.03734 seconds
copy 32768 sectors using a blocksize of 2048 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.28208 seconds
copy 32768 sectors using a blocksize of 4096 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
1.84449 seconds
copy 32768 sectors using a blocksize of 8192 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
1.68435 seconds
copy 32768 sectors using a blocksize of 16384 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
1.60814 seconds
optimal blocksize is 16384 sectors (8.00 MiB)
copy 19240128 sectors using a blocksize of 16384 sectors  18:17    ( SUCCES )
     	
19240128 of 19240128 copied
19535040 sectors copied
check filesystem on /dev/hda3 for errors and (if possible) fix them  01:40    ( SUCCES )
     	
e2fsck -f -y -v /dev/hda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

132292 inodes used (21.62%)
1892 non-contiguous inodes (1.4%)
# of inodes with ind/dind/tind blocks: 8235/464/0
1911938 blocks used (78.30%)
0 bad blocks
1 large file

102750 regular files
13733 directories
69 character device files
26 block device files
2 fifos
366 links
15694 symbolic links (14813 fast symbolic links)
9 sockets
--------
132649 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:04    ( SUCCES )
     	
resize2fs /dev/hda3
     	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 2441880 blocks long. Nothing to do!

calculate new size and position of /dev/hda3  00:00    ( SUCCES )
     	
requested start: 9398025
requested end: 156296384
requested size: 146898360 (70.05 GiB)
new start: 9398025
new end: 156296384
new size: 146898360 (70.05 GiB)
check filesystem on /dev/hda3 for errors and (if possible) fix them  01:37    ( SUCCES )
     	
e2fsck -f -y -v /dev/hda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

132292 inodes used (21.62%)
1892 non-contiguous inodes (1.4%)
# of inodes with ind/dind/tind blocks: 8235/464/0
1911938 blocks used (78.30%)
0 bad blocks
1 large file

102750 regular files
13733 directories
69 character device files
26 block device files
2 fifos
366 links
15694 symbolic links (14813 fast symbolic links)
9 sockets
--------
132649 files
e2fsck 1.40.8 (13-Mar-2008)
grow partition from 9.32 GiB to 70.05 GiB  00:05    ( SUCCES )
     	
old start: 9398025
old end: 28933064
old size: 19535040 (9.32 GiB)
new start: 9398025
new end: 156296384
new size: 146898360 (70.05 GiB)
check filesystem on /dev/hda3 for errors and (if possible) fix them  01:37    ( SUCCES )
     	
e2fsck -f -y -v /dev/hda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

132292 inodes used (21.62%)
1892 non-contiguous inodes (1.4%)
# of inodes with ind/dind/tind blocks: 8235/464/0
1911938 blocks used (78.30%)
0 bad blocks
1 large file

102750 regular files
13733 directories
69 character device files
26 block device files
2 fifos
366 links
15694 symbolic links (14813 fast symbolic links)
9 sockets
--------
132649 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( ERROR )
     	
resize2fs /dev/hda3
     	
resize2fs 1.40.8 (13-Mar-2008)
Please run 'e2fsck -f /dev/hda3' first.


```

---

### Post by mssever on 2008-08-27
Hmm... Your output says that you have 1 large file. I wonder if that somehow got created as a result of the error.

Try running baobab to see if there's some big file where you don't expect it.

---

### Post by Jonie on 2008-08-27
Beware! I am not responsible for any damage you may do to the filesystem.

It seems from the last successful operation, that the filesystem was indeed moved to the left:

old start: 9398025
old end: 28933064
old size: 19535040 (9.32 GiB)
new start: 9398025
new end: 156296384
new size: 146898360 (70.05 GiB)
check filesystem on /dev/hda3 for errors and (if possible) fix them  01:37    ( SUCCES )
     	
In the next turn Gparted was not able to grow the filesystem. Hardy uses somewhat outdated version of Gparted, which has some bugs when doing overlapped moves.

Download a livecd vith a more recent version of GParted such as Parted Magic or System RescueCD.

Then:

First delete and recreate the partition with EXACTLY THE SAME parameters below using command line parted.

old start: 9398025
old end: 28933064
old size: 19535040 (9.32 GiB)

Edit: Those sizes are given in blocks, i.e. 512 byte chunks. Parted has "unit s" command that enables you to use those sizes "as is".

Use the MKPART and NOT MKPARTFS command since the latter will delete your filesystem.

Then start GParted from the downloaded livecd and grow it again. But... beware!

---

### Post by nathanscottdaniels on 2008-08-27
> **Jonie said:**
> Beware! I am not responsible for any damage you may do to the filesystem.

It seems from the last successful operation, that the filesystem was indeed moved to the left:

old start: 9398025
old end: 28933064
old size: 19535040 (9.32 GiB)
new start: 9398025
new end: 156296384
new size: 146898360 (70.05 GiB)
check filesystem on /dev/hda3 for errors and (if possible) fix them  01:37    ( SUCCES )
     	
In the next turn Gparted was not able to grow the filesystem. Hardy usses somewhat outdated version of Gparted, which has some bugs when doing overlapped moves.

Download a livecd vith a more recent version of GParted such as Parted Magic or System RescueCD.

Then:

First delete and recreate the partition with the EXACTLY THE SAME parameters below using command line parted.

old start: 9398025
old end: 28933064
old size: 19535040 (9.32 GiB)

With MKPART, NOT MKPARTFS since this will delete your filesystem.

Then start GParted from the downloaded livecd and grow it again. But... beware!

Can I get someone else to confirm this before I try.  Anyone?

---

### Post by Jonie on 2008-08-27
For a safer run:

Note down start and end, also the faulty one in case you should undo. Check whether the partition is healthy after trimming. Switch the unit to sectors in parted.

---

### Post by nathanscottdaniels on 2008-08-27
> **mssever said:**
> Hmm... Your output says that you have 1 large file. I wonder if that somehow got created as a result of the error.

Try running baobab to see if there's some big file where you don't expect it.

That program didn't find anything wrong.  No huge files, nothing.  It incorrectly thought my HDD was only 20 GB big also.

I am still waiting for a second opinion on Jonie's suggestion.

I am not worried about loosing my data, (I would never put anything important on Ubuntu in case something bad happens like now) it's my setting I am worried about.  It took me literally 100 hrs of work to get Ubuntu to run on my laptop and another 100 hrs to pimp it out (customize it to my liking.)  is there anyway to backup the ENTIRE file system?

---

### Post by mssever on 2008-08-27
> **nathanscottdaniels said:**
> I am still waiting for a second opinion on Jonie's suggestion.I'm not able to offer an informed opinion on that. It sounds drastic, but it might work. But since I have no experience with anything like that, my opinion isn't worth much.

> is there anyway to backup the ENTIRE file system?
Assuming you have another available ext3 fielsystem (or another native *nix fs), you should be able to use ```
sudo cp -ar
``` to get an exact copy of all the files, and another sudo cp -ar to restore. I think you can also use tar for this, but I have no experience using tar for that purpose. Using cp won't preserve inodes and stuff like that, but it's sufficient to be able to restore your system (though you'll have to manually install grub, and you'll probably have to adjust the UUIDs in /etc/fstab).

---

### Post by Jonie on 2008-08-27
I can't make you sure it will work, but:

From the output one can see, that resize2fs didn't touch the partition as it seemed dirty to it. So you're left with the filesystem moved to the... left ;) My suggestion to bring back the old size is to make sure that partition size matches that of the filesystem.

You may also read this post:

[http://ubuntuforums.org/showthread.php?t=898160]("http://ubuntuforums.org/showthread.php?t=898160")

But I strongly discourage you to do a forcible resize. Trimming is pretty safe, as the resizing process found the filesystem dirty and extited.

Remark:

Don't copy a live system. Use livecd.

cp -arpPx would: copy a - all files, r- recursively, p - preserve symlinks, P - preserve permissions, x - stay on one filesystem

But it may not be sufficient to copy special files. Better look on the net for a tutorial that involves using tar.

F.ex.:

[https://help.ubuntu.com/community/BackupYourSystem/TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR")

---

### Post by nathanscottdaniels on 2008-08-28
Well I can't say much for your English but IT WORKED!!!

It took me ages to figure out that the numbers you gave me were in sectors and not bytes like parted was looking for and it took me ages to figure out what a sector WAS as well as how big they are.  And then it took me ages to find a calculator that could handle such a large number.  BUT IT WORKED!!

Also, GRUB got confused and I had to reinstall it.

---

