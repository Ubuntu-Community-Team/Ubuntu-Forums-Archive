---
title: "Slow overwrite with WD Caviar Green WD30EZRX"
date: 2012-11-10
forum: Hardware
---

### Post by lllllll on 2012-11-10
Hi, I have some strange issue with 12.04 LTS server and WD Caviar Green WD30EZRX drives.

the normal speed is a little slower than what I would expect from the drive

sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   8432 MB in  2.00 seconds = 4219.06 MB/sec
 Timing buffered disk reads: 254 MB in  3.01 seconds =  84.33 MB/sec


however, when I check it with dd I get

$dd if=/dev/zero of=testfilede2.out bs=1M count=100
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 0.112156 s, 935 MB/s

but if I overwrite the file, the speed is much slower
$dd if=/dev/zero of=testfilede2.out bs=1M count=100
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 1.28474 s, 81.6 MB/s

The controller is a 3.0Gbps Ports via ESB2 Controller

---

