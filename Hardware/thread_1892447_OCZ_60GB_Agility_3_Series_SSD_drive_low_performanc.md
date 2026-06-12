---
title: "OCZ 60GB Agility 3 Series SSD drive low performance?"
date: 2011-12-08
forum: Hardware
---

### Post by _Pete_ on 2011-12-08
Just got new hardware:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816115072](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115072)

and to attached to it this drive:

OCZ 60GB Agility 3 Series SSD drive.

It is supposed to deliver speeds:
Reading: upto 525 MB/s (SATA 6Gbps)
Write: upto 475 MB/s (SATA 6Gbps)

According to tests below, speeds are not even near to what is promised. 

Is there something you need to tune, either in the SSD drive or in the HighPoint Rocket 620 card. 
According to dmesg the  HighPoint Rocket 620 card is already working in 6Gbit mode ...

```

# bonnie++
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
corei7       32080M  1148  98 126598  11 74273   9  5334 100 229733  15 13116 160
Latency             15865us     554ms     483ms    4473us     434ms    2480us
Version  1.96       ------Sequential Create------ --------Random Create--------
corei7              -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 23322  22 +++++ +++ 24000  16 +++++ +++ +++++ +++ +++++ +++
Latency              1343us     924us     603us     633us     102us     625us
1.96,1.96,corei7,1,1323305088,32080M,,1148,98,126598,11,74273,9,5334,100,229733,15,13116,160,16,,,,,23322,22,+++++,+++,24000,16,+++++,+++,+++++,+++,+++++,+++,15865us,554ms,483ms,4473us,434ms,2480us,1343us,924us,603us,633us,102us,625us
petria@corei7:/tmp$ sudo -i

# hdparm -tT /dev/sdd
/dev/sdd:
 Timing cached reads:   20266 MB in  2.00 seconds = 10143.33 MB/sec
 Timing buffered disk reads: 484 MB in  3.01 seconds = 160.89 MB/sec


```

---

