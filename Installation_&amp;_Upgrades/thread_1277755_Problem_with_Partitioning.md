---
title: "Problem with Partitioning"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by poker158149 on 2009-09-28
I'm not sure if this is the right place to post this, but I'm having partition troubles.

Right now, I have one partition and Ubuntu is installed on it.

I'm trying to install Windows 7 on my computer, but when I tryto install it over my Ubuntu partition, it tells me that I need to format the partition to an NTFS format.

Well, I can't do that.

So what I did was, using GParted in Ubuntu, created a partiton table over my Ubuntu partiton so I cleared it out.

Now I'm trying to create a partition with NTFS format.

Everytime I try to, it gives me and error.

It always fails on the part where it has to create the NTFS table.

```
GParted 0.4.3
 Libparted 1.8.8
    **Create Primary Partition #1 (ntfs, 149.05 GiB) on /dev/sda**  00:00:21    ( ERROR )             create empty partition  00:00:11    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 312576704
size: 312576642 (149.05 GiB)[/I]          set partition type on /dev/sda1  00:00:10    ( SUCCESS )             *new partition type: ntfs*          create new ntfs file system  00:00:00    ( ERROR )             ***mkntfs -Q -v -L "Win7" /dev/sda1***             [I]/dev/sda1 is mounted.
Refusing to make a filesystem here!
[/I]             ========================================

```


How am I supposed to format it if it's the only OS I can have mounted?

---

### Post by earthpigg on 2009-09-28
hi,

you ***are*** running gparted from a LiveCD and unmounting the hard drive & all partitions first, right? just want to make sure... :D

and, have you simply considered wiping all partitions & tables and letting the windows install cd work with that?

---

### Post by poker158149 on 2009-09-28
>  you ***are*** running gparted from a LiveCD and unmounting the hard drive & all partitions first, right? just want to make sure... :grin:

Um.. no..

I installed it on my Ubuntu.

It won't let me unmount anything.

> and, have you simply considered wiping all partitions & tables and letting the windows install cd work with that? 	

Tried, but I can only install Windows on an NTFS formatted partition, which cannot be done because of the point of this post

---

### Post by presence1960 on 2009-09-28
you can't format a mounted partition - which is exactly what you are trying to do. You need to boot the Ubuntu Live CD or gparted Live CD to format Ubuntu's partition(s) or even to delete them leaving the entire disk as unallocated space. The OS will not allow you to unmount itself, for obvious reasons.

---

### Post by poker158149 on 2009-09-28
Well, after a while I realised it was because I'm using Ubuntu that it won't let me partition it. 
So, if I boot from my Ubuntu set-up disk, it'll let me format the partiton?

---

### Post by presence1960 on 2009-09-28
> **poker158149 said:**
> Well, after a while I realised it was because I'm using Ubuntu that it won't let me partition it. 
So, if I boot from my Ubuntu set-up disk, it'll let me format the partiton?

now you got it! proceed...

---

