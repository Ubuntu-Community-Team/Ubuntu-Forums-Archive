---
title: "How do you start from scratch?"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2009-07-20
I messed it up, now it will only boot into a terminal-like full screen where it refuses to do anything. I tried re-running the CD but it tried to partition again. How do I tell it to overwrite one of the existing partitions?

Or how can I delete the partition and start from scratch? 

The main problem was lack of space, so how do I tell it to give me a custom install (no open office or abiword, no games, etc)? 

Mariane

---

### Post by bacil on 2009-07-20
1. what exactly you want to achieve eg. protect existing data ?

2. there is advanced button on bottom of the screen before you click on last next and i believe that there you are able to select packages

---

### Post by merlinus on 2009-07-20
You might look into the barebones installation.  Apps can be added afterwards.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If you select manual at the partitioning screen, you should be able to see your existing partitions and select which one to install into.

---

### Post by Mariane on 2009-07-20
I saw the partition but was not able to select it. I am currently trying to increase it and defragmenting takes ages... But hopefully when it is done I will be able to undo the partitioning and then redo it again. 

The minimal CD look promising, but which should I choose among : 
Jaunty Jackalope
Intrepid Ibex
Hardy Heron
Dapper Drake
?

---

### Post by merlinus on 2009-07-20
I always like to use the latest version, but sometimes there can be conflicts.  Gives me something to do....   :D

---

### Post by earthpigg on 2009-07-20
it doesn't sound like what you want is a minimal install, but i could be mistaken.

> I tried re-running the CD but it tried to partition again. How do I tell it to overwrite one of the existing partitions?

using the regular vanilla ubuntu 9.04 normal desktop CD, select that partition to install to, and it will overwrite that partition.


obviously, back up anything you want to keep from that ubuntu install first.

---

### Post by Mariane on 2009-07-20
5 hours later... 

I got nowhere with the defragmenters (I installed and ran several on xp, but every time I tried to install ubuntu it wanted to create a partition of 2.5 GB only). I had about 15 free GB according to xp and I didn't dare override the 2.5 GB limit. Until I got so fed up... 

Then I manually dragged the partition until the available space was 10 GB. And Ubuntu installed itself fine, xp is still running,  everything looks OK :). 

So, for anyone interested:
- defragment using the windows defragmenter
- install defrag-a-file (either $7 or torrent) and tell it to defrag for space. Not the files, the point is to maximise empty disk space. 
- Boot on the linux CD
- When it says "starting the partitioner" it will tell you it has X GB of free space. Don't believe it and drag the cursor to the left until you give your partition the size you want, according to the empty space you know you have. 
- Hope for the best. 

It worked for me, for you I don't know. Backup everything first. If you backup, you won't need a backup. If you don't backup you will need one. 

Mariane

---

