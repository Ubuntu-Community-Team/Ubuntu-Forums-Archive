---
title: "partitioning for a nub"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by iameatingjam on 2005-12-23
I'm really new to anything to do with linux, I started checking it out 3 days ago, anyway I downloaded the kubunto live cd which was suggested on another board. I love it and want to install it, I have no place to backup my data though. I have a 3rd part application of which I bought for just this ( it wasn't cheap) it makes partitions without having to delete the whole drive. I made one but don't know how to use it. Its called diskstudio. Anyway, how do i use an already partition volume? I'm on mac os x btw, if that matters. Sorry if this sounds stupid and the answer is staring me in the face.

---

### Post by dcast on 2005-12-23
IF you want to install it you will have to download the kubuntu install cd image then during the install process you can pick which partition you want to install on

---

### Post by iameatingjam on 2005-12-23
I have, but it doesn't show the partition I made, just the whole drive.

---

### Post by roelofs on 2005-12-28
For what it's worth, I had almost the same problem:  an extended partition (originally created in 2000, I think) with multiple logical partitions within it; fdisk, Slackware 9, and Slackware 10 all saw everything just fine.  Ubuntu 5.10 did not.  No matter what I tried, it could not penetrate the extended partition; it persisted in showing it only as "primary" with "no filesystem detected" (or something like that).  Best guess is that Ubuntu can't understand the "W95 Extended" variant of extended partition, though that seems like a bit of a long shot...

Clearly there's a bug in Ubuntu's partitioning tool, but that's about all I can offer--I was unable to find a solution, although I came across some others with the same problem.  (I'm currently doing an exhaustive crawl through this site...only 36 more pages to go, sigh.)

---

### Post by psusi on 2005-12-28
You didn't need to waste your money on that tool, ubuntu is capable of spliting the disk without destroying the data.  I sugest that you blow away the partition you already created for it and go through the install process and tell it to use the unpartitioned space and it will take care of the rest.

---

### Post by Herman on 2005-12-28
I use the Ubuntu Installer's partitioning tool for playing around with on a test computer I have here, and some days I re-partition my disk three or four times in one day, experimenting and doing crazy things with different partitioners.
It's a hobby of mine, and I spend a lot of time at it.
Ubuntu installer's partitioning tool is my absolute favourite, and Gparted on the 'Live CD' is good too, I'm still learning that one. I also like QTParted on my Knoppix Live CD. I'm just about to give Mandriva's  'Disk Drake' a run in a few minutes, I haven't tried that one yet.
I have never tried 'Partition Magic' or any other non-linux partitioner, and have never had one bit of trouble *-ever-* with partitioning.
:D (Herman)

---

### Post by Herman on 2005-12-28
Today I am still working on an experiment to see how many operating systems I can install and run on a 30.0 GB disk.
Over several days, so far I have used Windows 98's fdisk, on the boot floppy, to format the new hard-disk and install Windows 98SE. Then Ubuntu Breezy, using it's own partitioner, Kubuntu, using it's own partitioner. Then I tried to install Vector Linux, but the downloaded .iso was faulty, so I had to abort that one. It didn't pass MD5sum. Then I used cfdisk with Zenwalk, and installed that, then Dapper Drake, using the Ubuntu Partitioner. Now I have finished partitioning with 'Disk Drake', and I'm in the middle of installing Mandriva. There's still plenty of more room on my disk here yet. Oh, and I forgot to mention, I have resized Dapper (on reiserfs) with QTParted, to enlarge it, and later resized it again smaller with 'Parted' from the console of the Ubuntu installer. I have also done experiments on the same disk earlier to make this How To:[http://www.ubuntuforums.org/showthread.php?t=105255]("http://www.ubuntuforums.org/showthread.php?t=105255")
That required several repeats of the same operations to get the instructions right. Then I did some experimens with Gparted. Then I did some more experiments with Gnu parted.
So far all these different partitioner seem to be 100% compatible, and I have not had a single hitch with any of them. 
I have been doing experiments like this for quite a long time now, more than one year anyway. My first ubuntu was 'Warty'.
I did mention that I have a new hard disk. The old one was over five years old, so was due for replacement anyway. Not many hard disks last that long. 
Looking for bugs is always a helpful thing to do, but I will be surprised if you find any.

---

### Post by Herman on 2005-12-29
Guess what! Talk about winning the lottery in reverse! I have a partitioning problem! ](*,)

It seems as though disk drake has hosed my partition table. I am now messing around seeing if I can learn more about the problem.
The partitioner on the Breezy installer CD shows an empty disk, and so does GParted on the Breezy Live CD. QTParted doesn't show anything and tells me there is an error, Parted says that another partitioner has made a faulty entry to my partition table or words to that effect....
Interesting.
Embarrasing, but interesting.
Mandriva runs fine, except it says I'm not on the sudoer's list, so that makes it hard to do much. Hmmm....:rolleyes:
As usual, I have to come back and apologize just when I get excited and get right out on a limb being so sure I am right. 
Sorry reolofs. I don't think it's a Ubuntu problem though, but I have got a problem of some kind. So I am not invincible after all. :(
(Herman)
EDIT: It's the same symptoms as reported here:[http://ubuntuforums.org/showthread.php?t=106642](http://ubuntuforums.org/showthread.php?t=106642)

---

### Post by Herman on 2005-12-29
Up date: I re-installed Breezy and then I put in Mandriva. This time it didn't do any harm to my partition table, because now I am installing Kubutu and it is going in fine. The existing partitions were all detected okay, so I cannot prove it is the fault of any partitioning software. Maybe it's just an error that occurs once in a while and can happen with any software, who knows.

---

