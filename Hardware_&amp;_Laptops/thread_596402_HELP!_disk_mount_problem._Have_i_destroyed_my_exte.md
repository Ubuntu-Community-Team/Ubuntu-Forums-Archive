---
title: "HELP! disk mount problem. Have i destroyed my external HD?"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by tpb03 on 2007-10-29
Help! I think i have lost all my backed up data, and ruined my external hard disk

I have a Seagate USB 300GB external hard disk which was not mounting in my recent install of 7.10.
I searched ubuntu forums and found the pmount info and ran the usual commands
I determined that my disk was /dev/sdb fat32 partition

i created a /mount/disk directory and attempted to mount my drive to it;

mount  /dev/sdb /mount/disk

which i found in a post. from this i got and error message stating that partition type was not determined.
Getting pretty frustrated again, i did another google search with my error message and found advice to type the following command

mkfs.ext3 /dev/sdb

I fear that this has wiped my external hd? Now the disk mounts up, but has only one folder (lost+found) which i cannot access. The disk states that it has 15gb used (it had 200gb used before) . Windows does not recognise the disk anymore and apparently the disk does not have a partition table either. Can i recover the lost data? and restore it back to FAT32?
If I have lost my data, how do I salvage the drive? Is it possible to reformat it and start again? how would I do this?
Please help!
Thanks

---

### Post by ddrichardson on 2007-10-29
try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by tpb03 on 2007-10-29
thanks, i found that in the repositories and i am running it now.
do you have any tips?
ie. is my hd still fat32 or will it recgnise as a linux partition?
what are the best options?

Thanks again

---

### Post by ddrichardson on 2007-10-29
Just follow the options, it's surprising how much it'll recover. I recently "got confused" repartitioning an external drive and deleted my laptops recovery partition. Test disk recovered it.

---

### Post by Linicks on 2007-10-29
Basically (hopefully) all that has happened is you changed the MBR.

What this means in real world terms is you ripped the index out of a book and put a new (but different) index there - hopefully the books pages are still intact.  What a conversion to ext3 does to a fat partition without using fdisk to index the drive as ext3 I don't know - but I do know fdisk reads a disk after using mkext3 on top of a fat partiton still as FAT.

So the partition table[s] is/are lost (I hope).  You need to be able to rebuild the fat32 MBR to reflect what is there.

Unfortunately you are pretty much on your own here.  Nobody can really help.  But my advice would be to sit on your hands and read what this app tells you.  Anymore tampering could destory all you data if it is still there, so take your time.

Nick

---

### Post by tpb03 on 2007-10-29
i just ran analyse, and it came back with nothing.
i pressed enter and moved through the options and it is analysing again and this time it has found a linux partition. How do you recover lost data? does it give you some options after the analyze finishes?

I am feeling very frustrated!
I **really** appreciate the help though. thanks

---

### Post by Linicks on 2007-10-29
Reading this thread:

[http://lists.debian.org/debian-user/2005/02/msg00219.html](http://lists.debian.org/debian-user/2005/02/msg00219.html)

Somebody ran mkfs.ext3 on a rieser partitioned disk.  I think you have lost your data...  But as I said, **don't** mess with it further.  Do some research, as it *could* be possible to recover.

Nick

---

### Post by ddrichardson on 2007-10-29
I'd cut your losses here. If testdisk can't find the previous partition then you're heading into professional (expensive) data recovery. Surprised someone suggested mkfs - it's equivalent to format in windows.

---

### Post by tpb03 on 2007-10-29
ok, i think it is fir to say that i have lost my data. it was a backup only anyway so i havnt lost anything (except my mp3 collection, but i can probably find a way to pull them back off my ipod, any hints here would be good!)

Question is now, how do i reformat the drive so its back to a clean fat32, so i can backup all my files (again!).
thanks

---

### Post by ddrichardson on 2007-10-29
mkfs.vfat /dev/sdb

---

