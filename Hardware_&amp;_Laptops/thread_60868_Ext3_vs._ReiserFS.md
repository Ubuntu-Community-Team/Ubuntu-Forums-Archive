---
title: "Ext3 vs. ReiserFS"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by tonysathre on 2005-08-29
i have installed ubuntu several times and have always used Ext3, but the other day i was reading about the ReiserFS filesystem and it said "although Ext3 looks like a good choice, pick ReiserFS because it is faster" so i installed ubuntu on a test machine and formatted it with ReiserFS and didnt notice any differences.  so i was just wondering what FS other people were using incase there is something that is better that i didnt notice, and also if there are any differences, what those differences are

---

### Post by c0rderr0y on 2005-08-29
i googled this a while back and there were  plenty of pros an dcons for each but i like ext3 try googling ext3 vs reiserfs its all about your preference.

---

### Post by DJ_Max on 2005-08-29
Ext 3 is the tried and tested Linux file system, and with journaling it's even better then Ext2. You won't a speed increase with ResierFS over Ext3 unless you have a lot of data.

If you haven't already, take a look at [http://www.tldp.org/LDP/sag/html/filesystems.html](http://www.tldp.org/LDP/sag/html/filesystems.html)

---

### Post by npaladin2000 on 2005-08-29
EXT3 started off as a hack of EXT2 that added journaling.  it's backwards compatible (readable as EXT2 to a kernel that can't read EXT3) but that adds overhead.  

ReiserFS has no such overhead and was designed from the ground up as a journaling filesystem.  It uses a database-like tree for file organization, and is optimized to handle small files at very high speed.  With larger files it takes a slight performace hit,  but with small files (like, for example, 6 million lib files and a bunch of .config files) ReiserFS is quicker than anything around.

XFS and JFS, from what I hear, do better with larger files.  Each filesystem has an area where it excels; otherwise we wouldn't have 4 of them (one of them would have won out).  You should make a choice based on your own particular needs.   Either ReiserFS or EXT3 are very good default choices....EXT3 will be a bit slower, but has that backwards compatibility.

Personally, I use ext2 or ext3 for my /boot volume, ReiserFS for my root volume, and usually ext3 or ReiserFS for my /home volume.  if you do a lot of work with large files (videos, DVD images, etc.) it might be worthwhile to have an XFS or JFS /home volume instead. 

Best thing is to play around and see what works better for you.

---

### Post by skoal on 2005-08-29
On my antiquated scsi 9 gig'er, reiserfs parsed 13,000+ files for filelight in < 35 secs.  That's slicker than snail spit.  Ext3?! adios, tortuga!

\\//_

---

### Post by incinerator on 2005-08-30
My experiences with ext3 and reiserfs (amongst others) where as follows:

I have a 5x300GB RAID-5 array that runs ext3. Benchmarks I run, (mainly bonnie++) did not suggest big performance gains with other filesystems. Therefore I chose ext3 as imho it is the most mature, stable and robust fs.

On my local Linux disks I used to go for ext3. I have tried reiserfs in the past, but that was quite a disappointing experience as reiserfs had big latency issues and desktop responsiveness was horrible, along with drop outs during audio playback whenever there was heavy hard disk operation.

That made me go back to ext3 again. Extr3 is performant enough for the normal user. It may be slightly slower but it is not putting such a heavy load onto the computer. Unlike reiserfs, I did not have latency and desktop responsiveness issues, either.

However, I recently started doing lots of compiling. The project I play around with is very big, on compilation run easily creates several gigabytes of new files, most of them being quite small. Re-building makes me deleting really large directories with thousands of small files in them. With ext3, that can take quite a while even with a well-tuned ext3 system (bigger journals etc.).

Therefore I chose to go for reiserfs when I switched from Arch Linux to kubuntu. So far the experience has not been to bad. The compilation stuff I am doing is a wee bit faster now, as reiserfs feels to be much quicker creating and deleting many small files. The latency issues are still there, but they are not so bad anymore, it seems the reiserfs code in the kernel has become better since I last tried reiserfs. However, I have experienced one major screw-up I cannot really explain. Recently, my / partition got read-only for some reason. A reboot would not work and in the end I had to boot the LiveCD to perform a manual fsck.reiserfs --fix-fixable to get my install to boot again. Warnings from fsck.reiserfs looked quite scary. However, it appears nothing has actually been lost.

As a "normal home user" I would always go for ext3. Imho ext3 is the most mature, stable and robust fs to use. I cannot speak for XFS and JFS because I only tested them on my server, but on a desktop ext3 still seems to kick reiserfs' behind when it comes to latency issues. And who likes jittery audio playback, anyway.

---

### Post by tonysathre on 2005-08-30
thanks for the advice, the last time i formatted a reiserFS volume my fstab looked like this
on a 60 GB HDD, which caused a dire problem

hda1-- windows xp with ntfs -- 27
hda2-- ubuntu mounted on / -- 3 GB
hda3--swap--2 GB
hda4 -- /home -- 28

the problem was that my / directory filled up in like 2 weeks, how can i make everything that i install, via synaptic, install in the /home dir

i know this is kinda off the subject so i am sorry for that

---

### Post by incinerator on 2005-08-30
In general I would not go for a separate /home partition on a desktop system. In my 7 years as GNU/Linux user I have yet to see any benefit of using more than one non-swap partition unless you want to exchange data or use LVM/EVMS.

Repartitioning is possibe, but needs care. I would boot the LiveCD and use qtparted (kubuntu) or gparted. These programs are frontends to parted, if you are not afraid of the command line you could try that. I haven't got much experience in using the gui tools and cannot tell how well they work.

Your setup is particularly tricky, with no quick simple explanation how to do it best. There are two problems with your particular setup:
1.) You have already used up your limit of four primary partitions, therefore it won't be easy to create intermediate partitions. As it is, you won't be able to create new partitons, at all (unless you delete others, of course).
2.) When resizing partitions, you cannot move the starting point of a partition.

One quick measure could be: Boot up the livecd, delete the swap partition, enlarge / by 1-1.5G, create a new swap partition in the remaining space. 2GB is more than generous for a swap partition, anyway. 512MB should be enough for a system with >=512MB RAM.

A note of caution: the LiveCD may be using your swap partition, if that is the case you will need to do a sudo swapoff /dev/hda3 first.

---

### Post by tonysathre on 2005-08-31
thanks for the advice, i havent used all 4 of my primary partitions, the numbers i gave above arent the actual partition numbers except for hda1 and hda2, the rest are all logical partitions.  usually when i repartition a HDD i use the ubuntu install cd, it seems to be the easiest tool ive ever used to repartition disks.  

about the size of my swap, how big of swap would i need for 512 MB DDR RAM. would a 512 MB swap suffice

---

### Post by incinerator on 2005-08-31
Imho 512MB RAM and 512MB swap is enough for all of the things you'll doing on a desktop. I would conisder adding more swap if you are running apps that really require much memory, emulation software like vmware for instance.

---

### Post by tonysathre on 2005-09-06
can i resize the swap just like any other partition using my install cd

---

