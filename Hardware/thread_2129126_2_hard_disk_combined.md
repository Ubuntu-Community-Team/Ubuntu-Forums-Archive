---
title: "2 hard disk combined"
date: 2013-03-25
forum: Hardware
---

### Post by sammurutto on 2013-03-25
I'm using Ubuntu 12.10 64bit. I have Windows-8 64bit installed as well.

I have 3 partitions, C:\, F:\, and G:\. The G drive is simple a recovery drive and 8GB is size -it's fine. The C and F drives are almost 40GB each. I save all my music and movies on the F drive. The C drive has my windows sytem and program folders. For some reason, Ubuntu combined the two drives (F and C) into one 75GB drive, and i can't find my music or movies anywhere (all the windows system and program folders are there).

However, when I reboot and start windows 8, all the drives are present.

Any help would be greatly appreciated -thank you.

---

### Post by bwallum on 2013-03-25
> **sammurutto said:**
> I'm using Ubuntu 12.10 64bit. I have Windows-8 64bit installed as well.

I have 3 partitions, C:\, F:\, and G:\. The G drive is simple a recovery drive and 8GB is size -it's fine. The C and F drives are almost 40GB each. I save all my music and movies on the F drive. The C drive has my windows sytem and program folders. For some reason, Ubuntu combined the two drives (F and C) into one 75GB drive, and i can't find my music or movies anywhere (all the windows system and program folders are there).

However, when I reboot and start windows 8, all the drives are present.

Any help would be greatly appreciated -thank you.

Could you explain the set up again please.

How many physical hard drives do you have?
Which drive and partition is Windows installed on?
Which drive and partition is Ubuntu installed on?

---

### Post by sammurutto on 2013-03-25
> **bwallum said:**
> Could you explain the set up again please.

How many physical hard drives do you have?
Which drive and partition is Windows installed on?
Which drive and partition is Ubuntu installed on?

I'm sorry by "2 hard disks combined" i actually meant "2 partitions".

To answer your questions: 1 physical hard drive. Windows on C: and Ubuntu on F:
Thank you.

---

### Post by Bashing-om on 2013-03-25
Well, as a start look at how ubuntu sees these partitions. Post the output of terminal code:
```
sudo fdisk -lu
```and take it from there.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by sammurutto on 2013-03-26
> **Bashing-om said:**
> Well, as a start look at how ubuntu sees these partitions. Post the output of terminal code:
```
sudo fdisk -lu
```and take it from there.[INDENT=3]
just try'n to help

[/INDENT]


I made another mistake. Both the F and C drives are almost 75GB each. So basically, my F drive is not showing (the one with the music and Ubuntu installed). Thanks for your help! The code is pasted below.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ed37f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   147091139    73545538+   7  HPFS/NTFS/exFAT
/dev/sda2       147091140   164425274     8667067+   7  HPFS/NTFS/exFAT
/dev/sda3       164425275   312576704    74075715    7  HPFS/NTFS/exFAT

---

### Post by Cheesemill on 2013-03-26
If this is a Wubi installation then the drive that the Ubuntu filesystem lives on is mounted on /host.

---

### Post by Bashing-om on 2013-03-26
sammurutto;
Additional  info -> a matter of semantics. In Windows designations of "drive a, drive b, drive c" are in actuality often the partitions on a single hard drive that in ubuntu is portrayed more correctly as 1st physical hard drive = sda, 2nd HD = sdb, 3rd HD = sdc (a,b,c) and the partitions on these physical hard drives are represented with a appended number; sda1 = 1st hard drive AND 1st partition; sda2 = 1st hard drive 2nd partition, sdc5 = 3rd hard drive 5th partition.

Now, your fdisk output; A single hard drive with only (3) Window's partitions(NTFS) on it. Thus the surmise that you have ubuntu installed inside of Windows as  "wubi".

I have no experience with wubi and therefore maybe of limited assistance. I will offer what I can if I can help.[INDENT=2]
your system, your operation -> what do you want to do 
[/INDENT]

---

### Post by sammurutto on 2013-03-26
> **Cheesemill said:**
> If this is a Wubi installation then the drive that the Ubuntu filesystem lives on is mounted on /host.

Thank you so much. I found all of my music :)

---

### Post by sammurutto on 2013-03-26
> **Bashing-om said:**
> sammurutto;
Additional  info -> a matter of semantics. In Windows designations of "drive a, drive b, drive c" are in actuality often the partitions on a single hard drive that in ubuntu is portrayed more correctly as 1st physical hard drive = sda, 2nd HD = sdb, 3rd HD = sdc (a,b,c) and the partitions on these physical hard drives are represented with a appended number; sda1 = 1st hard drive AND 1st partition; sda2 = 1st hard drive 2nd partition, sdc5 = 3rd hard drive 5th partition.

Now, your fdisk output; A single hard drive with only (3) Window's partitions(NTFS) on it. Thus the surmise that you have ubuntu installed inside of Windows as  "wubi".

I have no experience with wubi and therefore maybe of limited assistance. I will offer what I can if I can help.[INDENT=2]
your system, your operation -> what do you want to do 
[/INDENT]


Thank you for all your help. I feel so incompetent :) But yes, apparently it is a "wubi" installation and I found what I was looking for. Thanks again!

---

### Post by Bashing-om on 2013-03-26
sammurutto;

Pleased things are working out for you. ubuntu is a different operating system but not hard at all to learn. Hang in there, just a matter of time.

Please mark this thread as solved, aids others seeking solutions and the helpers time.
Interim Method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction:==>[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)[INDENT=3]
Happy ubunt'n

[/INDENT]

---

