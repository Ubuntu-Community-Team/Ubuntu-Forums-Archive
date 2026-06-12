---
title: "hard drive test...this cant be right"
date: 2010-02-18
forum: Hardware
---

### Post by 98cwitr on 2010-02-18
I have a plain Seagate 500GB and it's a few years old and I was thinking about going SSD. Just out of curiosity I wanted to see what specs this one has, so I ran this:

> sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   10950 MB in  2.00 seconds = 5484.53 MB/sec
 Timing buffered disk reads:  314 MB in  3.01 seconds = 104.48 MB/sec


104.48MB/sec read? I've run the tests several times with the same results. At $300+ for a decent sized SSD, it might not be worth it, I just want to boot in 6 seconds :D

---

### Post by tgalati4 on 2010-02-18
Put your computer in suspend mode and it will wake in 6 seconds.  New disks are fast--better controllers and higher data  density.

---

### Post by tommcd on 2010-02-18
> **98cwitr said:**
> I have a plain Seagate 500GB and it's a few years old and I was thinking about going SSD. 
If you are interested in the performance of SSD drives in linux, Phoronix has done several reviews of SSD drives:
[http://www.phoronix.com/scan.php?page=article&item=linux_ssd_performance&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_ssd_performance&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel_x25e_ssd_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_x25e_ssd_linux&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel_x25e_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_x25e_filesystems&num=1)
[http://www.phoronix.com/scan.php?page=article&item=ocz_vertex_ssd&num=1](http://www.phoronix.com/scan.php?page=article&item=ocz_vertex_ssd&num=1)

---

### Post by 98cwitr on 2010-02-18
looking at that it wouldnt  be worth it in the first place

---

### Post by 98cwitr on 2010-02-19
ok getting some different review results for linux OSs...SSD are yielding so really nice gains. 

[http://blogs.zdnet.com/perlow/?p=9190](http://blogs.zdnet.com/perlow/?p=9190)

---

