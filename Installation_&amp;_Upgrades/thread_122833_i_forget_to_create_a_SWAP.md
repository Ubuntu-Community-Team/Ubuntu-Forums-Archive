---
title: "i forget to create a SWAP"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by kojikabuto_l on 2006-01-28
In the instalation process i "forget" to create a Swap partition ( dont ask why :cry: )
now kubuntu runs ok, but sometimes almost freeze, 
the memory is 99% used always 
_____________________________________________________________
load average: 0.17, 0.15, 0.15
Tasks:  81 total,   1 running,  80 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.3% us,  2.3% sy,  0.0% ni, 69.0% id,  0.0% wa,  0.0% hi,  1.3% si
Mem:   1036520k total,  1005756k used,    30764k free,    79016k buffers
Swap:        0k total,        0k used,        0k free,   502392k cached
__________________________________________________________


can make a file swap now without create a new partition?

---

### Post by BjornW on 2006-01-28
As far as my knowledge goes, you'll need to create a partition to have a swap space. However you can do without swap space, but I would certainly not encourage you to do so. 

Swap space is essential a part of the harddisk where the computer's operating system can write some parts of its memory that hasn't been used lately to disk in order to free up some memory for other processes. Therefor you computer will work without a swap space but, it will behave slower than with a swap space. Sometimes it might even freeze or behave akward as you have noticed.

I would recommened to create a swap space and this can still be done.

Before you do anything make sure you have a **working backup** of all your important data!! 

You can do so by resizing the current partion and create some space for another partition (the swapspace). Rule of thumb for the size of the swap space is about 1,5 times the amount of memory your computer has. 

For example:

My computer has 512MB of memory, the swapspace should be 1,5*512MB = 768MB according to this rule.

[gParted]("http://gparted.sourceforge.net") supports (not for all filesystems though) the resizing of partitions and can help you with this, so you don't need to delete the current partition.

Hope this helps you out.

---

