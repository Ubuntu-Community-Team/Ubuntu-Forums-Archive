---
title: "Which format to use when installing Ubuntu?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by dan2714 on 2009-03-29
When manually setting up partitions, I am given the choice of several different formats. Which one is the best one, and should each partition use a different format? I am installing Ubuntu 9.04 Beta from DVD.

These are the different choices:

EXT2
EXT3 Journaling
EXT4 Journaling
ReiserFS
JFS Journaling
XFS Journaling

The last time I messed with Linux was back in 2003, it only used EXT3. I'm way behind since I haven't kept up with the latest versions.

I bought a new 1.5tb HD from Newegg and I have XP on C partition and Vista on D partition. I'm gonna delete the Vista partition and install Ubuntu so it will dual boot between XP & Ubuntu. If you have any tips or suggestions I would appreciate it (before I screw things up....  :lolflag: )

I have XP backed up with Norton Ghost on a separate drive so I can always start over. (been there, done that..... a bunch!)

---

### Post by cariboo on 2009-03-29
I would suggest using ext4, as it is much faster than ext3. Don't use reiser as it is in it's death throes. Nobody is working on it since Hans Reiser went to jail.

Jim

---

### Post by dan2714 on 2009-03-29
Thanks for the info.

I just read an article about Hans Reiser, the man was a genius, now he's in jail possibly for the rest of his life. What a waste.

---

### Post by Bakon Jarser on 2009-03-29
ext4 is brand new.  I'm not sure if there is even a tool for reading ext4 files from windows so you may want to look into that if you need to share files between os's.

---

### Post by zvacet on 2009-03-30
**Ext3** it still default file format for Ubuntu.

---

