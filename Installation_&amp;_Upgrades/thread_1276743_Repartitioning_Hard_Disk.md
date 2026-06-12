---
title: "Repartitioning Hard Disk"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by tckrapp on 2009-09-27
I am new to Ubuntu and bought the book " Beginning Ubutu Linux" by Keir Thomas and.... When I got to the step of repartioning on page 56 I ran into a problem. The authors indicate that I would have an option of resizing my main partition. However, I only had two options; either use the whole partition or  manually resizing. I am afraid of manually resizing and wiping out my Windows system. 
Some background info:
I am running windows xp professional on a Dell inspiron 8100 with a 40 gb hard disk.
I have approx. 27 gb free and I have defragmented several times. The visual graphic results show a large  contiguous space, although there are two blocks of unmovable files.One is towards the beginning and one approx 2/3 towards the end. I assume this bar graph represents the physical space on the disk.
I have tried to install with the 9.04 that came with the book and from a cd that I burned from a download. Both with the same result.
I want to have a dual boot option.
I do have some bad sectors on the disk- not many.

I have ordered a 60 gb drive.
I am planning on using fdisk and setting two partitions before installing windows and then trying the 9.04 install on this new drive. I can wait untill then but still would like to finish the installation on my present drive. 

I appreciate any thoughts on my present drive or on my future installation. Thanks 
Thomas Krapp

---

### Post by stlsaint on 2009-09-27
we need some more info on the problem you stated.> I have tried to install with the 9.04 that came with the book and from a cd that I burned from a download. Both with the same result. 
Also you need to make a partition out of that 27gb its prolly showing as unallocated space right now. boot to the livecd if you have internet run 
fdisk -l in a terminal and post the results here. This is assuming you dont have any partitions correctly done...if i am wrong please give some clarification on what it is you need. Also see my links below for more indepth help on dual booting.

---

