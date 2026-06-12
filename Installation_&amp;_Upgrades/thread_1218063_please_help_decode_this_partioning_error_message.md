---
title: "please help decode this partioning error message"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by adamgram on 2009-07-20
Okay I'm no expert by any stretch but I have installed Ubuntu a few times.  I think my hard drive might be shot.  Here's what I did:

I had a dual boot setup with Windows XP and Ubuntu.  Windows started loading to the "blue screen of death" and Ubuntu had some issues with flash and my sound card and was never really set up properly, so I decided to start from scratch.

First I installed Windows overwriting the entire disk, which worked fine.  I then went to partition off a section and install Ubuntu, however GParted (which I used through the Ubuntu Live disk under system-->administration-->partition editor) would not allow me to resize the partition and gave me an error message saying there was an error on the partition.  So I ran the 'memory test' from the Ubuntu boot disk and it found nothing.  

So, I decided to go about it the other way, I installed Ubuntu overwriting the entire disk, which worked fine, and I then used the same method to resize the partition to accommodate Windows.  The resizing step seemed to be working, then it gave an error message and told me to 'save details' for support.  Those details are listed below.  At the end it says "Error while reading block at sector 66420799".  Does this mean there's an error on my hard drive?  Thanks in advance.




```
GParted 0.3.8

Libparted 1.8.9

Move /dev/sda1 to the right and shrink it from 71.80 GiB to 35.90 GiB  00:21:42    ( ERROR )
         
calibrate /dev/sda1  00:00:00    ( SUCCESS )
         
path: /dev/sda1
start: 63
end: 150577244
size: 150577182 (71.80 GiB)
calculate new size and position of /dev/sda1  00:00:00    ( SUCCESS )
         
requested start: 75296655
requested end: 150577244
requested size: 75280590 (35.90 GiB)
new start: 75296655
new end: 150577244
new size: 75280590 (35.90 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:01:30    ( SUCCESS )
         
e2fsck -f -y -v /dev/sda1
         
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

122860 inodes used (2.61%)
1345 non-contiguous inodes (1.1%)
# of inodes with ind/dind/tind blocks: 5991/58/0
1039600 blocks used (5.52%)
0 bad blocks
1 large file

92914 regular files
13681 directories
69 character device files
26 block device files
2 fifos
497 links
16152 symbolic links (14686 fast symbolic links)
7 sockets
--------
123348 files
e2fsck 1.41.3 (12-Oct-2008)
shrink filesystem  00:13:12    ( SUCCESS )
         
resize2fs /dev/sda1 37640294K
         
Resizing the filesystem on /dev/sda1 to 9410073 (4k) blocks.
The filesystem on /dev/sda1 is now 9410073 blocks long.

resize2fs 1.41.3 (12-Oct-2008)
shrink partition from 71.80 GiB to 35.90 GiB  00:00:01    ( SUCCESS )
         
old start: 63
old end: 150577244
old size: 150577182 (71.80 GiB)
new start: 63
new end: 75280652
new size: 75280590 (35.90 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:58    ( SUCCESS )
         
e2fsck -f -y -v /dev/sda1
         
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

122860 inodes used (5.21%)
1439 non-contiguous inodes (1.2%)
# of inodes with ind/dind/tind blocks: 5991/58/0
891057 blocks used (9.47%)
0 bad blocks
1 large file

92914 regular files
13681 directories
69 character device files
26 block device files
2 fifos
497 links
16152 symbolic links (14686 fast symbolic links)
7 sockets
--------
123348 files
e2fsck 1.41.3 (12-Oct-2008)
grow filesystem to fill the partition  00:00:00    ( SUCCESS )
         
resize2fs /dev/sda1resize2fs 1.41.3 (12-Oct-2008)
The filesystem is already 9410073 blocks long. Nothing to do!

calculate new size and position of /dev/sda1  00:00:00    ( SUCCESS )
         
requested start: 75296655
requested end: 150577244
requested size: 75280590 (35.90 GiB)
new start: 75296655
new end: 150577244
new size: 75280590 (35.90 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:58    ( SUCCESS )
         
e2fsck -f -y -v /dev/sda1
         
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

122860 inodes used (5.21%)
1439 non-contiguous inodes (1.2%)
# of inodes with ind/dind/tind blocks: 5991/58/0
891057 blocks used (9.47%)
0 bad blocks
1 large file

92914 regular files
13681 directories
69 character device files
26 block device files
2 fifos
497 links
16152 symbolic links (14686 fast symbolic links)
7 sockets
--------
123348 files
e2fsck 1.41.3 (12-Oct-2008)
move filesystem to the right  00:05:03    ( ERROR )
         
using internal algorithm
copy 75280590 sectors
finding optimal blocksize
         
copy 32768 sectors using a blocksize of 64 sectors  00:00:03    ( SUCCESS )
         
32768 of 32768 copied
3.3351 seconds
copy 32768 sectors using a blocksize of 128 sectors  00:00:03    ( SUCCESS )
         
32768 of 32768 copied
3.18169 seconds
copy 32768 sectors using a blocksize of 256 sectors  00:00:03    ( SUCCESS )
         
32768 of 32768 copied
2.93488 seconds
copy 32768 sectors using a blocksize of 512 sectors  00:00:03    ( SUCCESS )
         
32768 of 32768 copied
2.52027 seconds
copy 32768 sectors using a blocksize of 1024 sectors  00:00:02    ( SUCCESS )
         
32768 of 32768 copied
2.04447 seconds
copy 32768 sectors using a blocksize of 2048 sectors  00:00:02    ( SUCCESS )
         
32768 of 32768 copied
1.52241 seconds
copy 32768 sectors using a blocksize of 4096 sectors  00:00:01    ( SUCCESS )
         
32768 of 32768 copied
1.26753 seconds
copy 32768 sectors using a blocksize of 8192 sectors  00:00:01    ( SUCCESS )
         
32768 of 32768 copied
1.13344 seconds
copy 32768 sectors using a blocksize of 16384 sectors  00:00:01    ( SUCCESS )
         
32768 of 32768 copied
1.1024 seconds
optimal blocksize is 16384 sectors (8.00 MiB)
copy 74985678 sectors using a blocksize of 16384 sectors  00:04:41    ( ERROR )
         
8548558 of 74985678 copied
Error while reading block at sector 66420799
8843470 sectors copied
libparted messages    ( INFO )
         
Input/output error during read on /dev/sda
```

---

### Post by presence1960 on 2009-07-20
next time after you paste text on here highlight all text and click the # sign on the toolbar to place code tags around the text like this :

```


GParted 0.3.8

Libparted 1.8.9

Move /dev/sda1 to the right and shrink it from 71.80 GiB to 35.90 GiB 00:21:42 ( ERROR )

calibrate /dev/sda1 00:00:00 ( SUCCESS )

path: /dev/sda1
start: 63
end: 150577244
size: 150577182 (71.80 GiB)
calculate new size and position of /dev/sda1 00:00:00 ( SUCCESS )

requested start: 75296655
requested end: 150577244
requested size: 75280590 (35.90 GiB)
new start: 75296655
new end: 150577244
new size: 75280590 (35.90 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them 00:01:30 ( SUCCESS )

e2fsck -f -y -v /dev/sda1

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

122860 inodes used (2.61%)
1345 non-contiguous inodes (1.1%)
# of inodes with ind/dind/tind blocks: 5991/58/0
1039600 blocks used (5.52%)
0 bad blocks
1 large file

92914 regular files
13681 directories
69 character device files
26 block device files
2 fifos
497 links
16152 symbolic links (14686 fast symbolic links)
7 sockets
--------
123348 files
e2fsck 1.41.3 (12-Oct-200
shrink filesystem 00:13:12 ( SUCCESS )

resize2fs /dev/sda1 37640294K

Resizing the filesystem on /dev/sda1 to 9410073 (4k) blocks.
The filesystem on /dev/sda1 is now 9410073 blocks long.

resize2fs 1.41.3 (12-Oct-200
shrink partition from 71.80 GiB to 35.90 GiB 00:00:01 ( SUCCESS )

old start: 63
old end: 150577244
old size: 150577182 (71.80 GiB)
new start: 63
new end: 75280652
new size: 75280590 (35.90 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them 00:00:58 ( SUCCESS )

e2fsck -f -y -v /dev/sda1

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

122860 inodes used (5.21%)
1439 non-contiguous inodes (1.2%)
# of inodes with ind/dind/tind blocks: 5991/58/0
891057 blocks used (9.47%)
0 bad blocks
1 large file

92914 regular files
13681 directories
69 character device files
26 block device files
2 fifos
497 links
16152 symbolic links (14686 fast symbolic links)
7 sockets
--------
123348 files
e2fsck 1.41.3 (12-Oct-200
grow filesystem to fill the partition 00:00:00 ( SUCCESS )

resize2fs /dev/sda1

resize2fs 1.41.3 (12-Oct-200
The filesystem is already 9410073 blocks long. Nothing to do!

calculate new size and position of /dev/sda1 00:00:00 ( SUCCESS )

requested start: 75296655
requested end: 150577244
requested size: 75280590 (35.90 GiB)
new start: 75296655
new end: 150577244
new size: 75280590 (35.90 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them 00:00:58 ( SUCCESS )

e2fsck -f -y -v /dev/sda1

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

122860 inodes used (5.21%)
1439 non-contiguous inodes (1.2%)
# of inodes with ind/dind/tind blocks: 5991/58/0
891057 blocks used (9.47%)
0 bad blocks
1 large file

92914 regular files
13681 directories
69 character device files
26 block device files
2 fifos
497 links
16152 symbolic links (14686 fast symbolic links)
7 sockets
--------
123348 files
e2fsck 1.41.3 (12-Oct-200
move filesystem to the right 00:05:03 ( ERROR )

using internal algorithm
copy 75280590 sectors
finding optimal blocksize

copy 32768 sectors using a blocksize of 64 sectors 00:00:03 ( SUCCESS )

32768 of 32768 copied
3.3351 seconds
copy 32768 sectors using a blocksize of 128 sectors 00:00:03 ( SUCCESS )

32768 of 32768 copied
3.18169 seconds
copy 32768 sectors using a blocksize of 256 sectors 00:00:03 ( SUCCESS )

32768 of 32768 copied
2.93488 seconds
copy 32768 sectors using a blocksize of 512 sectors 00:00:03 ( SUCCESS )

32768 of 32768 copied
2.52027 seconds
copy 32768 sectors using a blocksize of 1024 sectors 00:00:02 ( SUCCESS )

32768 of 32768 copied
2.04447 seconds
copy 32768 sectors using a blocksize of 2048 sectors 00:00:02 ( SUCCESS )

32768 of 32768 copied
1.52241 seconds
copy 32768 sectors using a blocksize of 4096 sectors 00:00:01 ( SUCCESS )

32768 of 32768 copied
1.26753 seconds
copy 32768 sectors using a blocksize of 8192 sectors 00:00:01 ( SUCCESS )

32768 of 32768 copied
1.13344 seconds
copy 32768 sectors using a blocksize of 16384 sectors 00:00:01 ( SUCCESS )

32768 of 32768 copied
1.1024 seconds
optimal blocksize is 16384 sectors (8.00 MiB)
copy 74985678 sectors using a blocksize of 16384 sectors 00:04:41 ( ERROR )

8548558 of 74985678 copied
Error while reading block at sector 66420799
8843470 sectors copied
libparted messages ( INFO )

Input/output error during read on /dev/sda
```

Much better don't you think?

---

### Post by prshah on 2009-07-20
> **adamgram said:**
> At the end it says "Error while reading block at sector 66420799".  Does this mean there's an error on my hard drive?  

I'd say there is. Here's how to confirm it: reboot using a live CD and run the badblocks test```
sudo badblocks -v /dev/sda1
``` This will perform a nondestructive test that will print out any badblocks that it finds. Note that this will make no changes to your filesystem! To fix (ie, tell the OS to ignore the bad blocks during future disk operations), you need another command (fsck -c). Post back the output of badblocks to see if you need this.

---

### Post by adamgram on 2009-07-20
> **prshah said:**
> I'd say there is. Here's how to confirm it: reboot using a live CD and run the badblocks test```
sudo badblocks -v /dev/sda1
``` This will perform a nondestructive test that will print out any badblocks that it finds. Note that this will make no changes to your filesystem! To fix (ie, tell the OS to ignore the bad blocks during future disk operations), you need another command (fsck -c). Post back the output of badblocks to see if you need this.

I will do this tonight.  Thank you.

---

### Post by raymondh on 2009-07-20
Another tip:

-defrag XP, hopefully pushing all its' data (except the unmoveable ones like MFT, etc) to the front of the partition.

Good luck.

---

### Post by adamgram on 2009-07-20
> **prshah said:**
> I'd say there is. Here's how to confirm it: reboot using a live CD and run the badblocks test```
sudo badblocks -v /dev/sda1
``` This will perform a nondestructive test that will print out any badblocks that it finds. Note that this will make no changes to your filesystem! To fix (ie, tell the OS to ignore the bad blocks during future disk operations), you need another command (fsck -c). Post back the output of badblocks to see if you need this.

```

ubuntu@ubuntu:~$ sudo badblocks -v /dev/sda1
Checking blocks 0 to 37640294
Checking for bad blocks (read-only test): 33215296done, 10:25 elapsed
33215300done, 10:49 elapsed
33215301
33215302
33215303
33215304
33215305
33215306
33215307
33215308done, 11:12 elapsed
33215309done, 11:36 elapsed
33215310done, 11:59 elapsed
33215311done, 12:23 elapsed
33215312
33215313
33215314
33215315
done                                
Pass completed, 17 bad blocks found.
ubuntu@ubuntu:~$ 

```

---

### Post by adamgram on 2009-07-20
I think this 
[http://ubuntuforums.org/showthread.php?t=715050](http://ubuntuforums.org/showthread.php?t=715050)
is telling me to replace the drive

---

### Post by prshah on 2009-07-20
> **adamgram said:**
> I think ... to replace the drive

> **adamgram said:**
> ```

ubuntu@ubuntu:~$ sudo badblocks -v /dev/sda1
Pass completed, 17 bad blocks found.
ubuntu@ubuntu:~$ 

```

For only 17 badblocks, I don't think you need to replace the drive. Even if you give it back in for warranty repair, all they will (might) do is remap the badblocks and return it to you.

You can safely remap the badblocks yourself with the fsck command. Boot off a live CD (because fsck should not be used on a mounted filesystem), then open a terminal and give the command```
sudo fsck -c -k -v /dev/sda1
``` This will re-perform the badblocks test and "mark" the bad blocks to prevent them from being used. You can specify a more thorough (and much longer) test by using "-cc" instead of "-c". I recommend you do this test if you have the time.

Once the badblocks are marked, you should have no further problems; however, if new badblocks crop up on a regular basis, then it's time to replace the drive.

Note that there is a tiny-to-small chance that you can lose data or programs with the above commands; so you do them at your own risk. A backup is a wise precaution.

I assume /dev/sda1 is an ext2/3/4/linux partition; if it is not, the format of the fsck command changes. Post back if this is the case.

---

### Post by adamgram on 2009-07-21
It's worth a shot... everything is backed up already.  Will I then have to do something similar in windows to block the windows OS from writing on the bad blocks or does this make changes to the disk that affect any operating system that is looking at it?

---

### Post by adamgram on 2009-07-22
> **prshah said:**
> For only 17 badblocks, I don't think you need to replace the drive. Even if you give it back in for warranty repair, all they will (might) do is remap the badblocks and return it to you.

You can safely remap the badblocks yourself with the fsck command. Boot off a live CD (because fsck should not be used on a mounted filesystem), then open a terminal and give the command```
sudo fsck -c -k -v /dev/sda1
``` This will re-perform the badblocks test and "mark" the bad blocks to prevent them from being used. You can specify a more thorough (and much longer) test by using "-cc" instead of "-c". I recommend you do this test if you have the time.

Once the badblocks are marked, you should have no further problems; however, if new badblocks crop up on a regular basis, then it's time to replace the drive.

Note that there is a tiny-to-small chance that you can lose data or programs with the above commands; so you do them at your own risk. A backup is a wise precaution.

I assume /dev/sda1 is an ext2/3/4/linux partition; if it is not, the format of the fsck command changes. Post back if this is the case.

seems to have worked!  thanks for your help!

---

### Post by prshah on 2009-07-22
> **adamgram said:**
> seems to have worked!  

Good to know. However. keep an eye on performance; if you find more badblocks, then you definitely need to change the HDD. Typically, a new badblock encountered will generate a DRDY error message in your dmesg (/var/log/messages). To keep an eye on this automatically, here's a little script I wrote```
#! /bin/bash
if [ `dmesg | grep -i -c drdy` -gt 0 ];
then
	touch /forcefsck
	logger "hdd_check: HDD check required, please restart system"
	notify-send -u normal -t 100000 -i info "HDD\ check" "HDD\ check\ required\ please\ restart\ system."
else
	logger "hdd_check: OK"
	notify-send -u low -t 10000 -i info "HDD check" "OK"
fi

```

You can save the script in /root/hdd_check.sh; then setup a cron job (crontab -e) to run it automatically, for example```
# m h  dom mon dow   command
37 8,14,20,3 * * * /root/hdd_check.sh
#this runs /root/hdd_check.sh everyday at 8.37, 14.37, 20.37, 3.37am

```

---

### Post by dhavalbbhatt on 2009-11-18
This seems to be an issue that I am facing too! Hopefully, I should be able to figure out if I have any bad blocks on my machine.

Thanks!

---

