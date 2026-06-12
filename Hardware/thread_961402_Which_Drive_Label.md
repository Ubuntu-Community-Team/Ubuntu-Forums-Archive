---
title: "Which Drive Label ???"
date: 2008-10-28
forum: Hardware
---

### Post by connord94 on 2008-10-28
I want to move my /home directory to it's own partition, but need to know which is my 29.5 gb partition from the following fdisk -

 Device Boot        Start         End      Blocks       Id   System
/dev/sdb1   *             1        3871    31093776    7   HPFS/NTFS
/dev/sdb2            3872        9729    47054385    5    Extended
/dev/sdb5            3872        9483    45078358+  83  Linux
/dev/sdb6            9484        9729     1975963+  82   Linux swap / Solaris


The partition is NTFS formatted, which makes me think it's sdb1, but according to that list thats the boot partition, but I don't boot from my 29.5 gb partition.


Any ideas which one?


Thanks,




Connor

---

### Post by nixscripter on 2008-10-28
Try opening a terminal and typing ```
mount
``` to get a listing of all mount points. If your home directory is a seperate partition, it should be in that list.

Hope this helps.

---

### Post by connord94 on 2008-10-29
My home directory *isn't* in a seperate partition, but I plan on putting it on one, thats why I need to know the drive label!

Hope that cleared any confusion.


Connor

---

### Post by cariboo on 2008-10-29
It looks like /dev/sdb5 is your linux partition, so that is the partition you need to split. Be sure to backup all the data in your home directory before attempting anything.

Jim

---

### Post by connord94 on 2008-10-29
I don't want to split any partitions, I already **have** one. I just need to know the label for it so I don't put my home partition in the wrong place!!!!!


Connor

---

### Post by connord94 on 2008-10-31
Any Ideas ?


Connor

---

### Post by Guille Damke on 2008-10-31
Just a guess, but if you do ```
df -h
``` you'll have in the output the mounting point and the size of your partitions in "human readable" numbers.

---

### Post by cariboo on 2008-10-31
So is your intention to use the partition that windows was on for your home directory?

Jim

---

### Post by connord94 on 2008-10-31
No, it was an empty partition, I **was** using it as a sort of transfer folder to swap things between linux and windows (dual boot). I've found out, it was sdb1, but I've came across a new problem after formatting it :@ . . .

[http://ubuntuforums.org/showthread.php?t=965351](http://ubuntuforums.org/showthread.php?t=965351)


Thanks, this thread can be closed now.


Connor

---

