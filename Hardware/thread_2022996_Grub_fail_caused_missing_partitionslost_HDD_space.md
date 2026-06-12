---
title: "Grub fail caused missing partitions/lost HDD space"
date: 2012-07-11
forum: Hardware
---

### Post by gopherkiler9 on 2012-07-11
hi there. I haven't messed with ubuntu in a long while, because of this problem.

what happened was i had ubuntu dual installed alongside my windows 7. I had grub as its main boot loader. I can't remember if i did the partitioning myself that time or not, pretty sure I did. However, for whatever reason, my grub loader failed once and it caused me to have to reset the mbr via a windows 7 disk. 

after I did this and ever since, the partitions I had set for ubuntu (a whopping 50gb) have been invisible to me. I KNOW they are there because my windows 7 says that my HDD says it is only like 418 in size. Clearly the memory is gone SOMEWHERE, but the partitions are not visible in either windows' partitioning tool, or when I load up a boot disk and use something like gparted.

any suggestions on what happened or how I can get my memory back? ive been making due with the missing memory, but its annoying me like a twitch.


as well, if this is in the wrong forum, its quite obvious how its a tough call between a software and hardware issue.


thanks.

EDIT: I must also mention that my dual boot worked just fine for the longest time. it then suddenly made me go through two screens to get to my ubuntu. (id click ubuntu, then it would give me options for what ubuntu as opposed to how it was originally of just clicking ubuntu once) then shortly after that (few days) the grub crash happened. it really had no reason to do that, so i am very confused as to WHY. I just want my memory back though. currently it only has windows 7 at startup and does NOT use grub.

---

### Post by ahallubuntu on 2012-07-11
If you want your Ubuntu dual boot back, just repair/update Grub using the same Ubuntu live CD you used to install.  After booting the live CD, I prefer the "chroot" method described here:

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

It's possible your Ubuntu partitions were encrypted(?).

If you just don't want Ubuntu anymore and want to go all-Windows 7 and reclaim the former free space, go into Windows disk management and you should see the space as a separate partition.  Windows can't natively see inside Linux partitions; all it can see there is a partition.  If you don't care about the information you had saved on your Linux partitions, just delete them with Windows disk management.  If something got corrupted, it may show up as unpartitioned free space already.

In any case, Windows 7 has a partition resize tool built in.  You  should be able simply to resize your Windows partition (the one with C: I guess) after you've deleted the Linux partitions.  You may have to delete the extended partition the Ubuntu installer probably created as well.  Then, you can resize to reclaim all of the space left over from Linux.

---

### Post by gopherkiler9 on 2012-07-11
thanks for the reply

i really dont want the ubuntu boot anymore on this computer and would really just want it back to full win7 (ive begun installing my linux versions on flashdrives instead of hard drives)

HOWEVER! the problem with the disk management is that it doesnt show any separate partitions. I KNOW theyre there because it shows that my main internal hdd is only 418 gb when in reality its a 500 (i know its not a full 500 due to memory loss, but I also know that loss isnt 82gb). When I look at my partitions (excluding any flash drives or externals plugged in) all I show is my 100 mb system reserve and a 465gb ntfs primary. thats it. nothing else. no other partitions of any sorts... but i KNOW theyre there.

as well as you can see, the partition editor admits that my hdd is atleast 465 gb big... but remember how ive mentioned that windows my computer says that i have X free of 418gb?

where did that remaning ~50 gb go? (my ubuntu partitions were only about 50gb big)



if what you say is true about them possibly getting encrypted.. that could be possible, but wouldnt I atleast be able to VIEW them in a partition editor?

---

### Post by gopherkiler9 on 2012-07-20
bump

---

### Post by oldfred on 2012-07-20
Post screenshot from gparted (attach with paperclip icon in edit panel) or this:

sudo fdisk -lu

---

### Post by gopherkiler9 on 2012-07-24
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36958aca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   976771071   488282112    7  HPFS/NTFS
root@ubuntu:/home/ubuntu# 


from what I am seeing, it shows that all the memory is there. even gparted  gives me a reading of 425gb used of 465. Windows doesnt show that I have a full 465 hard drive. it gives me that lesser reading. 
but gparted only gives me 2 partitions and an unallocated. its not showing the partitions as being there, but windows says the memory is gone.


/dev/sda1 is |     ntfs        |              | system reserved |100mb | 33.59mb used
/dev/sda2 (key symbol) |ntfs | /media/204204B420417E4|    | 465.66gb| 425.7gb used

---

### Post by oldfred on 2012-07-24
Windows does not show LInux partitions as it cannot read them. But your fdisk says you only have two partitions. The Windows (hidden) boot/repair and the main install.  Usually Windows computers also have another partition for the recovery partition and perhaps a vendor utilities partition.

Your fdisk also shows all sectors in the partitions, so there is no more space for additional partitions. You many have small amounts of unallocated at the beginning or end of drive.

Did you install with wubi? Wubi is just a file inside Windows NTFS partition that works like the full install but is not a true dual boot as it is not a separate partition.

---

### Post by gopherkiler9 on 2012-07-24
I didn't install with wubi on this computer. I believe I did the quick install using a live disk. I know windows cant see linux partitions, but even when I used a fedora live flash drive I can't see the ubuntu partitions, as well when I use a ubuntu live disk I cannot see them. Either way, I either manually partitioned it or I did the quick partition for about 40 gigs. But no.. not wubi

this here is an image of my contradictions within windows. [http://i182.photobucket.com/albums/x27/gopherkiler9/sizecontradiction.jpg](http://i182.photobucket.com/albums/x27/gopherkiler9/sizecontradiction.jpg)

i know it cant SEE the partitions... but windows knows something is there. And no matter what partition tool I use, I cant see that they there either. But clearly SOMETHING is occupying that memory. and it just so happens to be the exact size as the partition I allocated for my ubuntu.

---

### Post by oldfred on 2012-07-24
Both say 39GB free. So I do not think you have an issue. Except that is not much free. Windows NTFS works best with 30% free. Just about stops at 10% free.

I do not know about Windows but various Linux tools are changing from MB to MiB where drive manufacturers use MB.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by gopherkiler9 on 2012-07-24
My problem is that as a hard drive partion, it is saying that it is a 465gb hard drive, but my computer says its a 418gb hard drive. If you notice, the top part of the disk manager says its a 418, but the bottom part says its a 465. Then my computer says its a 418. I've got different readings in multiple places. When I made the Ubuntu partitions,  I shrunk the windows partition about 40 or 50 gb,  now that the partitions got corrupt,  my computer still says the memory is missing, 
but the partitions appear to be right. ONE of the two are giving me a wrong reading.

---

### Post by oldfred on 2012-07-25
Have you recent run chkdsk?

Windows has the partition start and size embedded in the NTFS partition boot sector. That has to match the partition table. Usually when they do not match Windows has issues. Then chkdsk updates PBR so Windows matches partition table.

---

### Post by gopherkiler9 on 2012-07-25
i did indeed chkdisk recently. I meant to do it on my external but it did it on the internal instead. All was fine =/

though currently I am having issues with windows updates, but that and this problem are totally unrelated.

---

### Post by oldfred on 2012-07-25
Your info in post #6 says all sectors on drive are in your two partitions. So it is something internal to Windows.

Perhaps a Windows forum would be better?
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

### Post by gopherkiler9 on 2012-07-25
> **oldfred said:**
> Your info in post #6 says all sectors on drive are in your two partitions. So it is something internal to Windows.

Perhaps a Windows forum would be better?
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

well what do you think could have done this then? one day, grub just couldnt do anything and wiped its self clean. I then had to reset my mbr using a windows recov disk. I never did anything with any of the old ubuntu partitions. so unless the grub error wiped them out too, then the've got to be there somewhere. but even if they were wiped out, wouldnt the memory go back to being unallocated? there is no way that grub error would have crashed grub, wiped out my ubuntu partitions, then resized my windows drive to incorporate the unallocated 40 gigs of memory.

---

### Post by oldfred on 2012-07-25
If you used Windows recovery not Windows repair, that would reset everything. 

A recovery disk restores the Windows to original. Windows repair will fix the boot loader, but does not see the Linux partitions and may just make them disappear.

Did you try testdisk as it can (somehow) find old partitions and show how disk was partitioned. If will often find many versions.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by gopherkiler9 on 2012-07-26
.

---

### Post by gopherkiler9 on 2012-07-26
> **oldfred said:**
> If you used Windows recovery not Windows repair, that would reset everything. 

A recovery disk restores the Windows to original. Windows repair will fix the boot loader, but does not see the Linux partitions and may just make them disappear.

Did you try testdisk as it can (somehow) find old partitions and show how disk was partitioned. If will often find many versions.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)




you sir, have made my day. 
testdisk found the corrupted partitions. I had 46gb of a missing linux primary (ubuntu) and 2gb of linux swap (still ubuntu)

after finding those partitions, i made them active again. I then had to run a check disk on my windows hard drive. This then fixed my boot as well as added those 2 missing partitions to the options shown in the partition editor. In the windows version, they came up as unallocated for the linux and as 'free space' for the swap.

i then right clicked on each of those 2 partitions and deleted them. Windows knew that those partitions housed info that windows couldnt read, but would be useful to other operating systems. 
After deleting both, I extended the partitions and now look.

[http://i182.photobucket.com/albums/x27/gopherkiler9/Untitled.jpg](http://i182.photobucket.com/albums/x27/gopherkiler9/Untitled.jpg)

all is how it is supposed to be. I WAS right. they WERE still there, just nothing could see them. 

many thanks.

---

### Post by oldfred on 2012-07-26
Glad that worked. 

Still now sure how Windows could not see it correctly, but the redo solved the problem.

---

