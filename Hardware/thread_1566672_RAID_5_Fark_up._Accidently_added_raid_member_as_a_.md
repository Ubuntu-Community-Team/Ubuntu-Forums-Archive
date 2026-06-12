---
title: "RAID 5 Fark up. Accidently added raid member as a spare."
date: 2010-09-02
forum: Hardware
---

### Post by t9999clint on 2010-09-02
OK this is my bad, as I probably shouldn't have been using the new disk utility for my Raid5 problem. But ether way I'm stuck and I need a bit of help here.

I found out this morning that my Raid5 was degraded because one of my WD 1tb blacks has started coming up with bad sectors. My server also started making this very quiet but still annoying clicking sound :sad: (I've lost several tbs of data before due to that clicking sound). So i figured dang, another drive failed.

Next I unmounted the Raid5 and started unplugging drives in order to figure out which drive was the dead one. Found the drive and unplugged it. Clicking noise gone... :)

This is where I made the stupid mistake... I seen the Raid5 was inactive now (since I was unplugging the drives trying to figure out which drive was reporting errors), so in order to mount it in degraded mode I told the new Disk utility thing to add one of the inactive drives back into the array. It did what I told it to, but little did I know that it did this by changing it into a spare drive fubaring the raid info in the beginning of the drive. #-o

So basically my problem is that I have a 5 drive Raid 5 array (4tb of not backed up data) where one drive failed and is now detached and another drive was mistakenly re-added to the array as a spare. Now the raid thinks 2 of the 5 drives failed and fails to mount.

What are my options here? Is there any way for me to change the spare back into a active raid member? Will RAIDExtract work with one drive missing and the other set as a spare? Or is my VERY large collection of backed up movies, music and games gone forever?

I don't have the money for 5tb worth of drives at the moment so the RaidExtract method is out for a while until I do.

---

### Post by Fafler on 2010-09-02
It might be possible. You should ask the linux-raid mailing list at [http://vger.kernel.org/vger-lists.html#linux-raid](http://vger.kernel.org/vger-lists.html#linux-raid)

You might be lucky that the only data changed when a drive is re-added as a spare is in the configuration file. Or atleast that only a bit of the data has been altered and it's possible to restore it.

---

### Post by t9999clint on 2010-09-02
Thx for the tip, there was a link to a wiki I'm reading over, there seams to be something called mkraid --force that can rewrite my superblocks, (which is what I think got overwritten). I'm gonna read up before I try it of course.

I'll keep you guys up to date in case someone else does the same stupid mistake I did.

---

### Post by t9999clint on 2010-09-02
apparently it's a fairly common mistake this thread seems to have a solution [http://ubuntuforums.org/showthread.php?t=410136](http://ubuntuforums.org/showthread.php?t=410136)
I have yet to test it however... I'm getting closer to a solution, and I'm not as freaked out as I was 8 hours ago...

Stay tuned... same bat time, same bat channel!

This was the info I was able to pull off the dying drive (R.I.P. little western digital, you lived a good life, and died while I still had a warranty on you).
```
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b1015d64:c4637495:aa1e97c1:81487361
  Creation Time : Thu Jun 17 15:35:51 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Sep  2 11:21:54 2010
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 1ccf86a4 - correct
         Events : 154822

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       49        5      spare   /dev/sdd1

   0     0       0        0        0      removed
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       17        3      active sync   /dev/sdb1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       49        5      spare   /dev/sdd1

```

---

### Post by t9999clint on 2010-09-02
using the info that the dying drive had on the old raid setup (aparently I farked up the other drives superblocks too) I was able to craft a command that was able to fix my issue.

```
 mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=5 missing /dev/sdf1 /dev/sdc1 /dev/sdb1 /dev/sde1

```[SIZE=4][COLOR=Red][U][B]
Remember that this command is merely an example, and that if you run this command on your computer you WILL erase things.
[/B][/U][SIZE=1][COLOR=Black]a[/COLOR][/SIZE][SIZE=1][COLOR=Black]lso, don't be like me. I am no pro. DON'T RUN WITHOUT BACKUPS!!! And NO a RAID5 DOES NOT COUNT AS A BACKUP!!

I'm just too poor for proper backups. I still use remote rsync to back up my work stuff though.
[/COLOR][/SIZE][/COLOR][/SIZE]

---

