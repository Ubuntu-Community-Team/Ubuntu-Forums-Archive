---
title: "Trying to understand disk usage"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by iogiuseppe on 2005-05-06
(I'm using 5.04 on a Dell Latitude C840)

I was copying some files via FTP from another machine (MP3s). According to Windows, it was exactly 17.3 GB (6305 files, 733 folders) worth. I started the copy and went to lunch. Before starting the copy, I looked at the System Monitor and saw that I had 29 GB of free space. When i came back from lunch, it had stopped caopying after only copying 16 GB, reporting that there was no more room on the disk. I looked to the System Monitor again and saw that it confirmed that there was 0 free bytes on the machine. So, I deleted the copied files to validate that it would return to 29 GB of free space (so that I wasn't dreaming) ... and it did.

So what's going on? 

How did I loose so much space so fast? I figured that it might be the number of files and their file size ... but they are all pretty big files (MP3s). 

Any thoughts?

---

### Post by nad on 2005-05-06
By default, when an ext3 filesystem is set up, 5% of the partition is reserved for the superuser. This can obviously be considerable in a large file system. Look at mkfs.ext3 and tune2fs to learn how to modify this value.

Also, have you taken out the trash lately?

---

### Post by iogiuseppe on 2005-05-07
Trash is definitely emptied.

Perhaps, I wasn't clear about my message, so I'll detail my steps below. 

1) Empty trash 
2) Check system monitor to see how much room I've got (30GB)
3) Start copying files 
4) Wait
5) Notice that it stopped, complaining that it was out of room. 
6) Look at system monitor to verify that I was out of room.
7) Check folder size on laptop and see that it says (16 GB)
8) Pause while thinking of what could have gone wrong and how I'm going to figure out what to do next.
9) Decide to delete the folder on the laptop and start over again 
10) Delete the folder, empty the trash, and check system monitor again ... whereby I see that i have 30 GB of space again ...
11) Ponder why copying 16 GB of files would make my system report that it was out of room ... and post to this 

Anyone else have any idea? 

I thought it might be the same type of "small file" problem (no better way of describing this comes to mind) where you have a large number of files that don't fit the allocation size of the disk so you waste a lot of space. But these are large files and there really aren't THAT many of them.

---

### Post by movery on 2005-05-10
If it was a small file problem then surely you wouldn't be able to create any files at all after the copy had stopped?  Could you?

Btw, I doubt this will solve your problem but is it possible to mount the remote filesystem and try and rsync the files?  Also, at a slight tangent try filelight if you want to find out where your disk is being used...its a fantastic disk utilisation visualisation program.  Only prob is that it needs kde installed to startup without errors :(

---

