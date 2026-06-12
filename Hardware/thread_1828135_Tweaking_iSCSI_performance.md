---
title: "Tweaking iSCSI performance"
date: 2011-08-18
forum: Hardware
---

### Post by KnevetS on 2011-08-18
I set up a server last night using 11.04, and since I had an extra disk in the box I decided to expose it via iSCSI and try out the Microsoft iSCSI initiator from my XP laptop.

I ran a benchmark, and writes were up between 40 and 70 MB/sec, reads were between 30 and 50 MB/sec. (single 1TB seagate baracuda drive)

Compared with a samba share that I have set up on another box, the numbers were promising.  Samba writes were abismal (< 10 MB/sec), but the reads were between 40 and  90 MB/sec. (3ware 9650 RAID on 4 samsung 500mb drives)

I really would like to figure out how to tweak iSCSI a bit more to get closer to natively hosted performance.  I have a whole new set of drives for my RAID array, and I'd really like to push the numbers up a bit.

Does anybody have some advice or a link to some light reading that would point me in the right direction?

I've attached screenshots of the benchmarks I took last night, including one for my locally hosted SSD.

---

### Post by TheR on 2011-08-20
I did't do any tweaking perticulary. I get 200+MB/s on hdtach test running  on windows server inside KVM with disks connected to iSCSI server. Disks are 4 raptors in RAID 10, 10Gb Ethernet, Ubuntu 10.04.

by
TheR

---

