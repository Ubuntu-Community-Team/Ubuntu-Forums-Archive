---
title: "installer wont resize partition"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by metalf8801 on 2009-08-04
I'm trying to dual boot Xubuntu 9.04 x86 and xp on a dell inspiron 6000 that already has Windows XP installed and I haven't set up a computer to dual boot in awhile but I still think something is wrong because when I get to the "Prepare disk space" I only get 3 options 
1st guided - use entire disk 
2nd Guided - use largest continuous free space (only 7 mb so not an option) 
3rd Manual. 

I like doing it manually anyway but when I try that option it tells me that the partition with xp on it is full and its not giving me an option to resize the partition.  Also its can't be full because its a 30gb drive with only 7gb used.  

to check if the CD was the problem I tried a CD that had ubuntu 8.10 on it and I ran into the same problem 

does anyone have any ideas of what I can do other then use Wubi? 

ps the partition type is NTFS 

Thanks 
Dan

---

### Post by merlinus on 2009-08-04
Delete temp files and empty /temp and /tmp directories, deactivate paging, and restart.  Delete pagefile.sys and defrag several times.  Then you may have more space to shrink xp.

---

### Post by metalf8801 on 2009-08-04
it turns out the problem is that the hard drive has to many bad sectors

---

