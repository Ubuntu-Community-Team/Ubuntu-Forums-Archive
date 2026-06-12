---
title: "Parted fooled me: need help trying to recover some data"
date: 2010-09-22
forum: Hardware
---

### Post by zazuzimbo on 2010-09-22
Short version: erased partition table, then recovered partitions with parted, but data was not back there. How is best to recover? Data may be recovered from another disk, wich temporarily had the same lost files. How to make partition images (with dd?) knowing the disk's start and ending sectors of each partition?

==============================================================

Hello,

I had a hard disk with some data on it, but I wanted to repartion this disk. So I moved its data do another one, and used parted to format and repartition the disk. Seeing the options I had I choose to create 3 FAT32 partitions and a "pc98" (over "msdos") partition table. I chose "PC98" thinking it would be better, but compatible with MSDOS tables... big mistake, as you will see. And the reason for FAT32 it that this HD is used on a very old computer, running Win98 (yes, it is still usefull for somethings).

As I was still in the same session, Ubuntu 9.04 promptly recognized the new 3 partitions just created with parted. So I mounted them from the "places" main menu. Everything fine. I moved the files back to the HD, to the first of the 3 partitions. Some data to the second one. Then I turned off the computer and put the HD on the old machine, and the bad part of the history begins. I know that a hardware failure is REALLY NOT THE CASE here, despite anything. So please do not answer with that in mind.


"PC98" is (as some of you may already know) imcompatible with Windows. So no partition showed up there. And so, physically moving the HD back to the Ubuntu 9.04 machine. But now, suprise: Ubuntu does NOT mount the partition again!! ... I was desperate. Looked like data loss... like HD failure. BUT, parted still sees everything as it was. FDISK doesn´t see no partition table (funny, for me). But how do I access those files now? :( Why Ubuntu did recognize and mounted automatically those partition with the PC98 table, and now it doens´t. Many tries of manual mounting, without any success.

Then, I made the "bigger mistake", I think. Using parted on the HD, I created a dos partition table (destroying the one there, of course), but relying on the "rescue" command of parted. This "pc98" thing spent more then 8000MiB with its partition table, so I thought: the FAT tables should be fine, as DOS partition table is smaller than this. I had the start and ending sectors for each partition on paper, to make sure no "wrong" partition was "recovered".

The recover command found my 3 "lost" partitions, and put them back in the partition table.

The sad part is that the data on the first partition (the most important data) wasn´t there! Partition came up empty. :( The second partition had the data intact, and the third was empty, as it was.

Now, can someone help me how can I recover some data? The data is (I think) still there. Is there some program that can scan the first partition's space, searching for file data?? On the good side, I think all files will be contiguous, as they were moved from the Linux in the begining (is this right?). Also, the files were copied to Ubuntu temporarily, so I may try to undelete some of them from Ubuntu's disk; I don´t know how would be best. I haven´t used the Ubuntu computer since then, thinking it might increase the undeletion there, if it will be needed.

I attach my terminal session with parted, so you might see more details.

Sorry for being long.

Thank you,

Zazu

Ps: may someone give me a command to create a disk image from the HD as it is now (for a partition) to preserve the data regardless of filesystem? Is "dd" command best for that?

---

### Post by Chame_Wizard on 2010-09-22
Did you use Gparted?

---

### Post by zazuzimbo on 2010-09-24
I know gparted. It wouldn´t change anything.

...

:(

---

