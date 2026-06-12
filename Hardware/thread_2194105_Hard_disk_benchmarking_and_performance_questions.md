---
title: "Hard disk benchmarking and performance questions"
date: 2013-12-16
forum: Hardware
---

### Post by devin0 on 2013-12-16
I picked up a 10 disk fibre channel array . I would like to benchmark its performance against my SCSI and IDE drives, any good program of choice you can recommend?

Also, I was told it was a hardware raid array enclosure, sadly its not, it only supports JBOD config unless i purchase an expensive addin card for it.
I was thinking of doing a software raid 5 config between some of the disks, would this be a big performance hit?

---

### Post by tgalati4 on 2013-12-16
*phoronix-test-suite* has a variety of benchmarks, including several disk I/O tests.  A simple command will give you some basic performance:

```
sudo hdparm -tT /dev/sda
```

On a crappy Acer laptop that was given to me:

tgalati4@Mint14-Extensa ~ $ sudo hdparm -tT /dev/sda
[sudo] password for tgalati4: 

/dev/sda:
 Timing cached reads:   1654 MB in  2.00 seconds = 827.12 MB/sec
 Timing buffered disk reads: 144 MB in  3.03 seconds =  47.54 MB/sec

The cache read is your RAM I/O speed--your upper limit of moving data around your system.

Generally hardware RAID is faster (and more expensive).  The amound of performance hit depends on the disk drives that you choose, their buffer and controller design and how fast they spin.  Crappy drives will give you crappy performance.

---

### Post by devin0 on 2013-12-17
Thanks. Nice little utility. Here were my results on a single FC disk.

/dev/sdh:
 Timing cached reads:   1012 MB in  2.00 seconds = 505.71 MB/sec
 Timing buffered disk reads: 104 MB in  3.05 seconds =  34.12 MB/sec

Not the fastest thing in the world, guess ill just have to wait for a raid controller and some faster disks to show up at a good price.

---

