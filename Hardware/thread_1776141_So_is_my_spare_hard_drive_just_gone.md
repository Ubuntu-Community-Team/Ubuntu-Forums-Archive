---
title: "So is my spare hard drive just gone?"
date: 2011-06-05
forum: Hardware
---

### Post by pileofcrap on 2011-06-05
So I just installed Ubuntu 2 days ago and honestly I haven't touched my Windows installation since. I'm seriously considering a complete switch. All that's needed is for me to find alternatives to applications which are vital for my job.

That said, I have a few external hard drives. One being a internal inside an enclosure. I had some trouble out of it previously and decided to yank it out of a laptop and use it myself.

I ran FSCK and got the following:
pileofcrap@ubuntu:~$ sudo fsck -pcfv /dev/sdb1
fsck from util-linux-ng 2.17.2
/dev/sdb1: Updating bad block inode.

      11 inodes used (0.00%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
  628697 blocks used (1.61%)
     113 bad blocks
       1 large file

       0 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       2 files



113 bad blocks... should I just remove it and throw it away?

---

### Post by Mark_in_Hollywood on 2011-06-05
Hmmpphhh! Fine question! Do you have data on this seemingly corrupted device backed up already? If you DO NOT CARE about the data, read on:

As you are asking for an opinion about what to do, rather than "HOW DO I FIX THIS", I suggest:

Run your 'puter in LiveCD mode. Have a look at the external drive by running GParted from System - Administration. If you like, you can reformat the device to ext3, ext4, NTFS, or whatever you like and you should repartition it as well. GParted is a GUI based applet and pretty easy to use (friendlier? for the rest of us).

USING GPARTED TO FORMAT AND PARTITION will wipe ALL YOUR DATA. You are warned. 

Once you get "happy" with the new formatting and partitioning, if it's a new enough drive, you can install 

[URL="http://packages.ubuntu.com/natty/smartmontools"[/URL]

Smart Monitor Tool and keep your knowledge "up to date" about that device.

---

### Post by tgalati4 on 2011-06-05
Run badblocks on the drive and make note of any.

Then run fsck with the -c parameter to mark them as bad so they won't get used in the future.

---

### Post by pileofcrap on 2011-06-05
Thanks for the help guys. That is what I was looking for. a way to perhaps save or make use of the drive. I'd hate to lose a whole 160GB of possible backup power. I do plan to only put stuff on there that is a necessity, videos I can download again, ect..

Update...
Shortly after making my first post I decided to do my own little test. I copied a few large files to the drive then ran another check. It says that 2 more bad blocks had appeared. I don't know how accurate the test is, though. I guess I gotta suck it up as a lost.

On the flip side, it's just an internal inside an enclosure. I'll just take out the drive and buy another one.

---

