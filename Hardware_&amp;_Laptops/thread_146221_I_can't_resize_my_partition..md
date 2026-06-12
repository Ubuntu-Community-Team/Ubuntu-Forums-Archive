---
title: "I can't resize my partition."
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by LinuxLove on 2006-03-17
This may not entirely concern Ubuntu, but I am in the process of installing it. Basically, I can't resize the partition Windows XP is on. I'm using Paragon Partition Manager 7.0 Professional, and after I try to resize the partition the results do not show. I still have a 148GB hard drive.

Thinking this was a program error, I loaded up the Ubuntu installer. When asked about partitions I went away to resize and it again did not work.

The partition is an NTFS with 51GB used. I tried to use the Windows defragmenter (r. click my computer - manager) and after I still could not resize.

I've googled my problem several times and I still can't find an answer.

Whats going on?

Thanks for your time

---

### Post by Xian on 2006-03-17
I would advise using the partition tool on the Ubuntu InstallCD.
I've never had an issue with it, but of course backups are essential.

---

### Post by LinuxLove on 2006-03-17
[QUOTE=Xian]I would advise using the partition tool on the Ubuntu InstallCD.
I've never had an issue with it, but of course backups are essential.[/QUOTE]

I did try that (the partition tool that comes up on the installer, correct?), and I still cannot resize my partition.

---

### Post by Xian on 2006-03-17
Did you get any error messages or any indication of what step failed?

---

### Post by LinuxLove on 2006-03-17
[QUOTE=Xian]Did you get any error messages or any indication of what step failed?[/QUOTE]


OK, I tried to do this again in the installation:

1. Tried to resize the main partition to 125gb.
2. A blank screen came up (blue) for no more than 5-7 seconds.
3. Brought me back to the partition tool.
4. No changes occured..

I then brought up my recovery partition (FAT32 - 6gb) and tried to resize it. I took a small amount of memory out, and that worked just fine.

So I'm thinking theres something wrong with my partition?

And I did not getting any error messages.

---

### Post by firecat53 on 2006-03-18
1. Try Qtparted on the Knoppix Live CD
2. Try the RIP Linux Rescue Disk version of ntfsresize. Follow the instructions closely and use the dry run feature first! I (lucky me) had an issue with my harddrive that prevented ntfsresize from functioning correctly. I ended up getting a development version from one of the developers. It worked, but corrupted the partition, rendering networking unusuable. End result --- I reloaded XP anyways.

So...I guess my recommendation is to try the Knoppix CD and/or RIP CD first. If that doesn't work, just back up your data and start over.

Good luck!
Scott

---

