---
title: "Ubuntu on T42 and Disk Geometry"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by Lobsterman on 2006-05-17
Hi everybody,

I have been trying to install Ubuntu 5.10 on a T42 with little luck so far. 

Its a T42 with a 100GB (new) HDD, which contains already an XP  (NTFS) and an IBM_Service partitions. It seems that the problem is the way by which the Ubuntu partitioner is treating the HDD since it has different CHS under XP and under Ubuntu. (XP: 12921,240,63, Ubuntu GParted: 12161,255,63). The instillation process goes fine and I can also boot XP, but exploring the HDD using TestDisk or Partition Magic reveals disk geometry inconsistencies (in fact, Partition Magic reports the entire disk ans "BAD" after the Ubuntu instillation). I should emphasize at this point that these inconsistencies DO NOT exist once I delete the newly created Linux partitions. I know that Partition Magic might be "wrong" but since TestDisk is also reporting inconsistencies I am afraid I might lose data if the HDD geometry used is wrong.

To explore this a bit further I used a Knoppix live CD and an Ubuntu 5.10 live CD to explore the HDD. Knoppix had no problem detecting the partitions on my HDD and I could mount and browse their contents. Ubuntu live CD did not detect the partitions and QParted reported the wrong disk geometry. I also tried creating the Ubuntu installation partitions in Partition Magic and then install using these partitions, but it did not make any difference. 

I have been looking for some info on this type of problems and could not find any workarounds or solutions.

Any ideas?](*,) 

Thanks!

---

### Post by mips on 2006-05-18
[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html) 
[http://forum.thinkpads.com/viewtopic.php?t=16839](http://forum.thinkpads.com/viewtopic.php?t=16839)
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_5.04_on_a_ThinkPad_T43_%281875%29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_5.04_on_a_ThinkPad_T43_%281875%29)

Sounds weird. I did a bit of googling and reading and did not come across a similair problem. have you tried the dapper cd maybe ? Maybe download the latest daily build of dapper, burn at x8 speed and try that. [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

The fact that knoppix is happy and ubunu not tells me something is not right, but what I dont know.

---

### Post by Lobsterman on 2006-05-18
Mips, thank you for your advice and for the links.

I tried to install Ubuntu 6.06 (both the beta version and the daily built) and both failed to install. I didn't go too much into the reasons for that.

On the other hand, I did make some progress with respect to the problem with the disk. Here is what I did:

1) installed Ubuntu 5.10 in the extended partition of my HDD. I created four partitions (/boot (35MB), swap (2GB), /root (15GB), and /home(20 GB))
2) installed GRUB on the /boot partition
3) Followed the doual boot instructions from [http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)

Result: a dual boot system. both Ubuntu and XP now boot. The IBM rescue and recovery partition also works :-).

However, I still have some inconsistencies in my HDD. under XP partition magic and testdisk still report inconsistencies. Under Ubuntu fdisk -l reports that the "partition doesn't end on cylinder boundary" with respect to the XP partitions. An easy answr would be that if both XP and Ubuntu boot then "who cares", but I do want to get to the bottom of this and understand if something is indeed wrong with my partition table.

Any idaes?

Thanks !

---

### Post by mips on 2006-05-20
**[COLOR="Red"]"partition doesn't end on cylinder boundary"[/COLOR]**

Paste the entire line above including the "" into google and it will return some results. Seems like a windows/linux thing. Might also wanna enable LBA hdd mode in bios iff possible to see if it makes a difference.

---

