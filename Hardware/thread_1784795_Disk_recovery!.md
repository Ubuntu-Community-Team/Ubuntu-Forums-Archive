---
title: "Disk recovery!"
date: 2011-06-17
forum: Hardware
---

### Post by Struki on 2011-06-17
Runing: Ubuntu 10.04 server + gnome desktop

I have 1 hdd with 3 partitions mounted at boot on the above OS. All partitions mount without any problems and partition tables seem to be ok. But, on the smallest partition I've lost all of my directory listing, seems they were somehow deleted, but the disk info states that there is a portion of disk still used, and the size is the same as the size of the folders missing. So the conclusion is they are still there but unacesable   

So I tried testdisk and i can find my folders as they where before, only they are colored red, and when i try to access them via testdisk i get "file system seems to be damaged". There seems no way for me to recover them to the original functioning state. I've tried photorec but i get them unnamed and all the meta data is lost. 

All of this happened after i reinstalled ubuntu server, all of the partitions were mountable and working exept the files were missing.

So my questions:
1. Is there something I haven't tried that would recover my files in there original state, considering they weren't deleted by hand, and what info should i provide

1. If i recover all the deleted files with photorec, is there a way to recover filenames and folders as well?

thanks ppl!

---

### Post by sakishrist on 2011-06-17
Hello there,

I have had some bad experience with lost data on HDDs as well and I have tried photorec.

What I know is that the program does not recover the file names (because as far as I know it does not look into the filetable to find the data). 

One thing I think would be helpful would be to provide the file system of that partition.

A suggestion I have would be to use a check dist utility (I do not have experience with the server edition so I do not know what utility it might have for the job). If the partition is M$ compatible it would be a fair idea to try the chkdsk on a windows OS. It might just do the trick. 

Another suggestion I have is to find a program that can do a backup of the whole partition (not just the files but even the "empty space") so that if something goes wrong with the check, you can at least restore it to the state it was before the check.

Good luck!!!

---

