---
title: "Out of disk space - or not?"
date: 2015-01-30
forum: Hardware
---

### Post by lile001 on 2015-01-30
I have been getting messages recently that I am out of disk space, less than 1 GB left.  However, when I investigate this issue, System Monitor reports that I have three drives, the first (where I am thinking the root filesystem lives and the complaints are referencing) has 8 GB of space, the second (where I do most of my day-to-day work ) has 61 GB and the third (which is only used as a local backup) has 190 GB.  Those sound like comfortable margins.  

System Monitor is about the only tool I know how to use to look into this problem, what other means might you suggest to find out why it is happening?  

Next time the error comes up I will append the message, and what steps I tried,  to this post.

---

### Post by ian-weisser on 2015-01-30
> **lile001 said:**
> I have been getting messages recently that I am out of disk space

Your error message is saying that a **partition** is out of space.
The complete error message, and the actions you take to get that error message, would be very helpful.

Use the 'df' command to discover which partition is low on space. Post the df output here.

---

### Post by yancek on 2015-01-30
An 8GB partition for the root filesystem is a little small by todays standards.  My recollection in installing Ubuntu 14.04 is that approximately 6+GB are needed for the base install.  If you have installed new software or added system files it won't take much to get to 8GB.

---

### Post by mooreted on 2015-01-30
Open a terminal and enter the following command:

df -h

---

### Post by lile001 on 2016-01-16
Thanks for the help folks.  I did get to the bottom of this issue using some of the commands mentioned above.  I finally decided it was time to upgrade anyway, and did a fresh install of Ubuntu on a new box with a generous and fast new SSD.  This time I am being careful to put the operating system on the SSD, and a few files that I might need to be zippy, but 99% of my data resides on a 1TB internal drive.  Now I know how to set this up, when I built the previous machine I didn't understand much about where things were being put.  As I solved some other problems at the same time - memory, data organization, doing some housekeeping, faster box, it was worth it to start from scratch.  Thanks.

---

