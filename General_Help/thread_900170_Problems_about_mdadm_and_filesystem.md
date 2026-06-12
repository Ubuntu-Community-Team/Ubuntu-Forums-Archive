---
title: "Problems about mdadm and filesystem"
date: 2008-08-25
forum: General Help
---

### Post by LittleCVR on 2008-08-25
Hello everybody, I'm new here.
I have encountered a serious problem about my RAID device.
So I'm here to ask if someone could help me, many thanks!


Yesterday, I decided to migrate from [COLOR="RoyalBlue"]Gentoo[/COLOR], which I had used for nearly 3 years, to Ubuntu.
And that is when my nightmare begins......

Firstly, about two years ago, I bought [COLOR="DarkOrange"]two 250G SATA hds[/COLOR], and I used mdadm to make a [COLOR="Blue"]RAID1 device[/COLOR] consists of them.

Then, about one year ago, I bought [COLOR="DarkBrown"]two new 250G SATA hds[/COLOR] again, so I had four 250G SATA hds in total at that time.
I used mdadm to make [COLOR="Blue"]a new RAID5 device[/COLOR] consists of all of them, including the two old ones.

[COLOR="Gray"]========== The Problems Begin Here ==========[/COLOR]
And so I began to install [COLOR="Sienna"]Ubuntu 8.04[/COLOR].
After I finished installing, I have discovered a very weired thing.

Say, I have four disks.
Two of them are newer, two of them are older.
The older ones were made into a RAID1 device long time ago.
Let's call the old ones [COLOR="Red"]sda[/COLOR] and [COLOR="Red"]sdc[/COLOR] (that's exactly the name Ubuntu gives me), and the new ones [COLOR="SeaGreen"]sdb[/COLOR] and [COLOR="SeaGreen"]sdd[/COLOR].

What I found out is that: Ubuntu is unable to detect the partition on [COLOR="Red"]sda[/COLOR] and [COLOR="Red"]sdc[/COLOR]! (the old ones)
That is to say, I saw only:
```
/dev/sda
/dev/sdb
/dev/sdb1
/dev/sdc
/dev/sdd
/dev/sdd1
```
in the /dev folder.

But fdisk could found that......
```
root@CVR-Linux:~# fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a500091

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect
```

Actually, mdadm was smart enough to detect any RAID devices made before, yet if the system could not detect the partitions, mdadm could not, either.

But surprisingly, mdadm found my old RAID1 device!
I don't know if that is the reason why Ubuntu could not detect my partitions on the old ones. (Because it stops after detecting a valid superblock that belongs to [COLOR="Red"]an entire disk[/COLOR]?)
Using "mdadm --examine /dev/sda", I can see the superblock information about my old RAID1 device!
(I did not type the wrong thing, it's [COLOR="Red"]/dev/sda[/COLOR], not [COLOR="Red"]/dev/sda1[/COLOR].
It seems that the superblock belongs to the entire disk, and luckily it was not erased during the last year, or it cannot be erased?
I don't know. I've already forgotten how I created the RAID1 device. Well......)


So I typed the following commands (I doubted that these cmds are the actual causes of my big problem......)
```
mdadm --zero-superblock /dev/sda
mdadm --zero-superblock /dev/sdc
```

After rebooting my system, Ubuntu could found the partitions!
So I assembled them together happily, think that: "Thank God, it's all passed!"
```
root@CVR-Linux:/home# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Feb 19 00:59:16 2007
     Raid Level : raid5
     Array Size : 732587712 (698.65 GiB 750.17 GB)
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Aug 25 14:28:45 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 6929bd92:7a0d05e7:396cde87:7bcf5317
         Events : 0.4618

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

```


[COLOR="Gray"]========== The Second Part ==========[/COLOR]
But after all of these, I cannot mount it!!!!!!
The system just keep saying that something like bad magic number or superblock, whatever, I don't remember it clearly.
In on words, the system does not think it is an valid ext2 or ext3 fs.

Alright, so I run e2fsck. (I don't know if this is another wrong step, too. Oh! I wish I didn't do anything yesterday!)
Because e2fsck could not found the superblock, either.
So I have no choice but assigned the position of superblock manually:
```
e2fsck -y -b 102400000 /dev/md0
```

(I don't know why but "e2fsck -b [COLOR="DarkOrange"]32768[/COLOR] /dev/md0" does not work. The block size should be 4k. So neither does "-b [COLOR="DarkOrange"]8193[/COLOR]" or "-b [COLOR="DarkOrange"]16384[/COLOR]" work, of course. The superblocks are deeeeeeeeeead already!!!!!!:(
The number [COLOR="DarkOrange"]102400000[/COLOR] was get from the command: "mke2fs -n /dev/md0", which will pretend to make an ext2 fs and show where the superblocks would be placed.)

e2fsck ran for the entire afternoon and night yesterday.
(I don't know whether running e2fsck is still another mistake I have made......)

Well......anyhow, I can mount it finally.
But that is still not the end.

=========== The Third Part ===========
After I mounted it.
I found that half of my data and files are gone!!!!!!

And e2fsck placed them into the folder "lost+found."
After listing the directory, it contains about 130 million files and dirs......(I'm pretty sure that I do not have so much data.)

It is really a mess, the folder looks like:
```
c--Sr-S-wx  1 1928663134   3171858954    19,     72 1911-09-14 03:15 #10010618
s-wx-ws-w-  1 3085929103   2612289613             0 2029-05-23 08:00 #10010620
sr-sr-S--t  1 1549437456   2824568782             0 1902-06-17 04:31 #10010651
b--x-ws-wT  1 1845045758   2461843428   166,     35 2016-03-21 12:58 #10010686
c-w---sr-T  1 3862310908   1810993455    95,    108 1927-06-08 08:44 #10010687
crwS-wSrwT  1 2313889467   3974642649   110,    233 2003-04-18 21:07 #10010740
cr-sr-xr-T  1  909374712   3076935307   108,    151 2000-09-23 01:57 #10010742
s--srwSrwT  1 3770032857   4282978649             0 1921-03-16 01:27 #10010749
c--srwSrw-  1 3453643748   3600606811   151,    159 1938-08-27 13:37 #10010751
s--x-w---t  1  946916521    308213798             0 1995-04-18 00:56 #10010770
c-wSrwsrw-  1 1142219929   2904977977   238,    180 1915-10-19 01:03 #10010776
sr-x--x--x  1 1340741656   2508160074             0 2029-02-22 12:21 #10010782
crwxr--rw-  1  994379158    299136597    32,     21 1928-09-08 16:39 #10010794
c--Srwx-wt  1 1495450870   3825820913   220,     76 2009-12-11 10:40 #10010826
b-wx--srw-  1 2052401579   3489293515    47,     94 1945-04-05 21:49 #10010843
c--x-wS-w-  1  114332495   2731369506   126,    126 1934-02-26 11:59 #10010854
c-ws-wS-wx  1 3023542489    324974406    86,    106 2005-05-11 21:05 #10010872
pr-sr----x  1 3407537597   4160148934             0 1986-07-24 18:12 #10010888
s-wsr-sr--  1 4246927255   3403829549             0 2035-05-08 10:07 #10010899
p-w-rwsr-T  1 3938491138   1059652813             0 2006-03-18 06:12 #10010927
s--x----wt  1 1099462254   3967150293             0 1915-06-22 13:11 #10010940
c--x-w---x  1 2801589982    160879892   237,    126 1981-05-25 19:55 #10010958
cr-Sr-sr--  1 1129008701   1017049432    55,     56 1973-03-25 20:28 #10010969
s-w---x--T  1 1900069622   3441167457             0 1955-09-25 23:22 #10010972
prwx--Sr--  1 1961040769   4099579401             0 1995-12-05 11:49 #10010995

```

Well......althought a mess, I still find some of them are useful.
[COLOR="Green"]But is there any way to turn a character device or block device into a regular file???[/COLOR]
If it is someway to do so,  I may rescue a bunch of data.

========== End ==========
Alright, I think that I have nearly no chances to rescue my data.:(
If someone has useful suggestions, please tell me, many thanks.

Anyway, it is really a catastrophe for me.

---

### Post by fjgaude on 2008-08-25
Your experience points to always having a backup near-line and off-line. What you have done is likely wreck the data and filesystem.

I can't say how you created the raid5 array. But as the rule, when a drive is in any array, you stop the array, then unmount it. Then run --zero-superblock drive-by-drive. And sda is not the same as sda1.

I don't know what filesystem you had on your array, which is put on after the array is assembled.

So many things to know before using software raid, eh? These are from where I learned:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
   [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

---

