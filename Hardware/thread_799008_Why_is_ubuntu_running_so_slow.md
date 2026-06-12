---
title: "Why is ubuntu running so slow?"
date: 2008-05-18
forum: Hardware
---

### Post by ed84c on 2008-05-18
Ever since I installed Ubuntu 7.1 to run parallel with Windows, ubuntu & windows have been running well below speed (mainly ubuntu). I'm gonna replace  the comp soon anyway, but in the short term I was wondering if anybody could help me out (i.e. what is at fault; HDD, RAM, CPU). I suspect it is the HDD/ partitioning that is at fault as neither CPU nor RAM seem to be overly demanded.

CPU = 2.6 GHz AMD athlon 
RAM = 2.25 Gb 

I did a bonnie++ benchmark on the HDD;

 ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ed-desktop    2528M 13817  95 22805  16 11871   9 16026  83 24374   6 152.2   2
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 20648  92 +++++ +++ 27576  93 21500  92 +++++ +++ 27810  90
ed-desktop,2528M,13817,95,22805,16,11871,9,16026,83,24374,6,152.2,2,16,20648,92,


Any ideas?
Ed

---

### Post by KOTAPAKA on 2008-05-18
I don't know about windows but if you do not configure the graphics deivers in Ubuntu 2H and do not get 3D acceleration then compiz will make it run reeeaaallly slowly.

---

### Post by ed84c on 2008-05-18
Ah that might be why, this did all seem to happen around the time I got a new  21" monitor. 

I'll have a look. Cheers.

---

