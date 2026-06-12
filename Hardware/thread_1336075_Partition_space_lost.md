---
title: "Partition space lost"
date: 2009-11-24
forum: Hardware
---

### Post by Gouz on 2009-11-24
Greetings all

I just update to 9.10 and everything was excellent. I made my root partition separate from my home one. Installed couple of things in root and then I was left out of disk space.

I gave the root partition 25Gb the total files in it is 11Gb and I am left with 1.1Gb free. Does any one know what happened and where the disk space is gone?

I tried to disk check, but since it is the root it is mounted.
I tried badblocks. but nothing useful there.

Any thought?

Gouz

---

### Post by Gouz on 2009-11-24
I just used df -Th

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     23G   21G  1,2G  95%

now the question, when I check the disk space it says that there is only 11G of data. And then (some data are unreadable)

---

### Post by garvinrick4 on 2009-11-24
So you have a dual boot and linux is on sda/1 instead of the
boot partion being there and Windows only likes Primary 1,2 or 3 and linux then would be sda/4 with sda/5 ubuntu and sda/6 swap.
Not in that order all the time but Windows does not like 4 and up
I do not believe.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by garvinrick4 on 2009-11-24
If you just have Ubuntu on a small drive Did it just make one partition or more. The whole drive is ext/4 now. More info I quess.
It does not do that for no reason.

---

### Post by Gouz on 2009-11-24
Okey first I do not boot anything else except Ubuntu

here is my fdisk

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3039    24410736   83  Linux
/dev/sda2            3040       14593    92807505    5  Extended
/dev/sda5            3040        3404     2931831   82  Linux swap/Solaris
/dev/sda6            3405       14593    89875611   83  Linux

More info:

seriously there is nothing more than what I said unless I am missing something. It was just fine and then I noticed that I was left with 1.1G.

When I right click in the file and go properties I see that the partition size is 11G used and 1.1G free space. But from the command line I see that I have 25G and 24G used space. When I examine the files from Nautilus I see nothing,same amount of file same amount of data (11G used space, 1.1G free space).

Partision /dev/sda1 is my root and the boot is there as well unless the * does not meant boot partition.

Gouz

---

### Post by garvinrick4 on 2009-11-24
So the Extended partion is about 25 and 5 and 6 add
up to 2 and the boot is in 1. You got 11 gig in 6 and it shows
that 6 has 23 gig or so. Wow that is a problem worth discovering
where it is hiding. Should not sda/1 show just the boot partition
and not the size of whole drive. And the extended sda/2 show the
size of sda/5 and sda/6 size minus the boot partition. I am used to dual
booting but I have not seen the boot partition the whole size of the drive. Maybe I am used to the dual boot partitioning.
I just did not think the boot partition would be where the file system would be mounted. I will look it up again on single boot.

---

### Post by Gouz on 2009-11-25
Okay I could not find anything about the problem.

No where is the forums or the net.

I end up formatting :( since I have a time limit. My computer had to be up and running with several software until this morning.

It is a shame that I couldn't find the solution. So for those that have the same problem in the future here as some notes.

A guide that will help you with lost space: 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

If nothing in that guide can not help you out to recover your Lost space then I am sorry but welcome to my world. To bad I could not fix it, good luck in your tries.


Gouz


PS. If any one has any idea on the matter even if it too late for me please post here so that the next one who may need it could have it :)

---

