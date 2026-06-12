---
title: "FAT32 harddisk fails - how can I repair it?"
date: 2009-08-02
forum: Hardware
---

### Post by nih_che on 2009-08-02
Dear all

This is my first post, I am new to Ubuntu and do not have much experience with the tools available. Here  I have a problem to which I have not found an answer using Google et al. 

I have a 500GB Lacie external harddisk which is FAT32 formatted (yes I am also using Windows :-)). I was copying some data from a Windows computer onto it and suddenly there was an error and it could not find the drive any more. When I tried to mount it, Windows Explorer would crash. It also made a very "unhappy" sound, a "ticking" or "clicking" kind of sound, like a clock.
Luckily I remembered that I had Linux (Ubuntu 8.10) as well and there it mounted fine and I just started copying whatever I could grab. At one point, the copying process became very slow and the ticking/clicking started again. I got all the data and during the rest of the copying process, the ticking vanished. Still there a some problems when mounting and the drive does not seem very reliable.

From my internet research (and my intuition) I concluded that the harddrive might be dying. Still I thought that only some sectors might be compromised especially since it only seemed to have problems at some locations of the drive. To check whats wrong with it, I used dosfsck and I got the following output

```

>> sudo dosfsck -r -v /dev/sdc1 

dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
Boot sector contents:
System ID "MSDOS5.0"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     32768 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
  61033472 bytes per FAT (= 119206 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 122083328 (sector 238444)
  15258274 data clusters (499983122432 bytes)
63 sectors/track, 255 heads
        63 hidden sectors
 976768002 sectors total
Got 6258688 bytes instead of 61033104 at 16384
>>

```thus it aborted with the last line. This does not seem to be a very good sign if the filesystem check aborts but I dont really get whats wrong or what happened at the line "Got 6258688 bytes instead of 61033104 at 16384"!
I found some other people with the same problem [http://forum.ubuntuusers.de/topic/filesystem-defekt/](http://forum.ubuntuusers.de/topic/filesystem-defekt/) and I followed the advice there to use the badblocks command to check for badblocks. Again the ticking noise and a lot of bad blocks. The output is (it is in a file but that is the same I guess) looks like this:

```

>>sudo badblocks -o out.txt /dev/sdc1 
6144
6148
...
6371
7128
...
7231
7728
...
7831
67080
67112
...
67119
67296
...
67303

```where "..." indicates that (nearly) all numbers in between were there. Since its late here in Europe I will let it run overnight, it found totally 300 such numbers so far (currupt sectors I guess) and the drive was clicking all the time while it found them but not during the check afterwords or before. But I guess the exact number of currupt sectors is not that important :-). So to me it looks like some part of the harddrive is currupted but not the whole drive. 

So what do you suggest that I should do - is the harddrive itself physically currupted or only the file system? Can I somehow restore the currupted sectors or do I have to reformat? If I reformat is the hardrive prone to failure sometimes soon in the future? 

Thanks a lot for your answers

---

