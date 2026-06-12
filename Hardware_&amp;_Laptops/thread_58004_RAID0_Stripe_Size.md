---
title: "RAID0 Stripe Size?"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by ganja_guru on 2005-08-18
im using the 3ware 8506-4LP with 4 WD 250 GB Caviar Drives.. What would be the ideal stripe size for :

-reiserfs
-reiser 4
-xfs

my options are from 64k all the way upto 1MB

ive read that 64k is ideal for windows..

with the 4-way raid, im getting 100MB/s in HDTach witha tripe size of 512KB (which seems a little low)

my current plan is to use 2 of the drives with a stripe size of 64k with windows and the other two with linux.. im a general desktop user, bit of divx encoding and lots of compiling. Im using the AMD FX-55 with 2GB of RAM

so what would be an ideal linux stripe size?

---

### Post by pmjdebruijn on 2005-08-18
I don't think much research has been done on that issue...

I can recommend a course of action to find out...

You can use a tool called **bonnie++** to benchmark your drive array... So I suggest:

1. Configure an array using stripe size *x*
2. Boot Linux
3. mkfs the array with filesystem *y*
4. mount the array on (for example) /mnt/array
5. run bonnie++ (pipe the output to ~/bonnie-*y*-*x*.txt or something like that)
6. unmount the array
7. reboot

Do this until you've tried all combinations, or at least, the most important ones...

I did do some generic filesystem benchmarks myself a while ago, you can find them here:
[http://www.xs4all.nl/~bruijn9/bench/fs/](http://www.xs4all.nl/~bruijn9/bench/fs/)
And for the IO schedulers:
[http://www.xs4all.nl/~bruijn9/bench/iosched/](http://www.xs4all.nl/~bruijn9/bench/iosched/)

Good Luck,
Pascal de Bruijn

PS: If you actually do these test, please post your results back to this forum... I'd certainly be interested!

---

### Post by ganja_guru on 2005-08-18
thanks for the info..so according to your tests 64k seems the fastest.. i will be booting ino ubuntu on a regular ide drive and mounting the raid0 array...so i should do a 

$ bonnie++ /mnt/raid (or whatever)

can you tell me what parameters you used for bonnie++.. im not too familiar with it..

---

### Post by pmjdebruijn on 2005-08-27
Hi,

bonnie++ has excellent parameter help, it's really trivial...

anyway parameters depend on your system, your test file size neem to be (at least) twice the size of your internal memory (RAM) to get accurate test results.

Regards,
Pascal de Bruijn

---

### Post by ganja_guru on 2005-09-06
my results are :

AcharyaX  1  4G  605  98  84920  23  46401  14  904  98  110006  22  315.3  4  16  9475  40  +++++  +++  8974  34  6654  29  +++++  +++  3542  14

AcharyaX  Latency  21843us  6385ms  221ms  32083us  21271us  160ms  Latency  24609us  66us  10936us  226ms  61us  339ms

i converted all of them into html using bon_csv2html and dont really know how to post them here, so i can only give u the csv's

anyway, block seq. output is 84920 w/ 23% cpu
Rewrite is 46401 w/ 14% CPU
block Seq Input is 110006 w/ 22% CPU and so on

the setting which worked the best were :

$ mkfs.xfs -f -d su=128k,sw=2 /dev/xxx

$ blockdev --setra 512 /dev/xxx (=> made a huge difference)


as i mentioned before, this is on a two disc RAID0 with 64KB stripe size. The only value i have a doubt with is the "Seq Output (per Char)" which is 605 K/s with 98% CPU usage.. is this because im testing with a large 4GB file?

XFS rules, btw..

---

### Post by ganja_guru on 2005-09-06
Hmm.. Seq Output hovers around 600 K/s when i reduce test file size also. Other file system tests give similar results.. most results on the web seem to have scores like 5000K/s or higher..any ideas?

---

### Post by ganja_guru on 2005-09-06
These results were obtained using :


bonnie++ -d /myidedrive/ -s 800 -r 400 -u root

which is my **IDE drive NOT on RAID0** 

i had to reduce ram and file size cause i dont have enough space on this drive..

all results seem consistent expect block sequential input which is it an insane 566685 K/s ..which is impossible..can anyone please explain whats going on?

Version 1.93c       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
AcharyaX       800M   496  87 34925  12 37639  16   868  99 566685  98  3144  39
Latency               753ms     380ms    9518us   18260us    8728us   95532us
Version 1.93c       ------Sequential Create------ --------Random Create--------
AcharyaX            -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16   100  99   199  99  1480  98   148  99   201  99   349  99
Latency             39390us   19146us   10730us   22799us   18930us   16815us
1.93c,1.93c,AcharyaX,1,1125982584,800M,,496,87,34925,12,37639,16,868,99,566685,98,3144,39,16,,,,,100,99,199,99,1480,98,148,99,201,99,349,99,753ms,380ms,9518us,18260us,8728us,95532us,39390us,19146us,10730us,22799us,18930us,16815us

---

### Post by ganja_guru on 2005-09-06
ok I've figured it out.. I was using a newer version of bonnie++ ( bonnie++2 1.93c) and that seems to still have some bugs which bugger up the SEq Output column and kills the last two digits.. hence 630 and not 63000... \\:D/  I still have no clue why the IDE drive gave such huge values though.. :?

---

