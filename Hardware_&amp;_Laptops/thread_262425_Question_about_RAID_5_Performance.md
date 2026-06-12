---
title: "Question about RAID 5 Performance"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by SticknClutch on 2006-09-21
Hello good people of the Ubuntu forums.

I have a 3ware 9590SE Raid Controller running a 750TB raid 5 array across 4 disks. Ubuntu installed perfectly and loaded the correct 3x-9xxx drivers.

What I don't get is how come im getting such poor performance out of this array. I did an hdparm and im only getting 65.96 MB/sec, that is only a slight performance increase over a single drive.

Later I booted up using the SuSE 10.0 Live DVD and hdparm showed 150MB/sec buffered reads!.

My question is, how do I increase this performance? What kind of tweaks do I need to make?

P.S. This is on a ext3 formatted system.

hdparm:
```
jose@python:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   2336 MB in  2.00 seconds = 1167.93 MB/sec
 Timing buffered disk reads:  200 MB in  3.03 seconds =  65.96 MB/sec
```

bonnie++:
```
jose@python:~$ sync ;sudo bonnie++ -n 0 -u 0 -r 512 -s 20480 -f -b
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
python          20G           44556  25 29190  12           70093   9  94.8   0
python,20G,,,44556,25,29190,12,,,70093,9,94.8,0,,,,,,,,,,,,,
```

lsmod:
```
lsmod | grep 3w
3w_9xxx                38432  4
scsi_mod              160504  6 sr_mod,sbp2,sg,3w_9xxx,sd_mod,libata
```

---

