---
title: "Disk performance"
date: 2009-12-09
forum: Hardware
---

### Post by don_eros on 2009-12-09
Hi there,

I'm trying to understand whether a) I'm expecting too much from my hard disks b) they just suck or c) there's something wrong with Ubuntu.

I have three SATA disks, one for the system, one for data and one external backup disk (connected via eSATA).

I've conducted this little experiment: I copied a directory containing 10 large files for a total of 11467944 bytes (~11 GB), between these filesystems:

sda7	ext4 (SATA)  -> Western Digital WD3000JS (300 GB)
sda8	ntfs (SATA)
sdb1	ext3 (SATA)  -> Seagate Barracuda ST31500341AS (1500 GB)
sdc1	ntfs (ESATA) -> Western Digital WD5000AAJS (500 GB)

These are the results of the various copy operations:

sda7    ->  sdc1
    real    5m23.286s
    user    0m0.320s
    sys     0m22.730s
    ~=      35 MB/s

sdb1    ->  sda7
    real    5m0.189s
    user    0m0.040s
    sys     0m7.050s
    ~=      38 MB/s

sdb1    ->  sda8	
    real    4m56.390s
    user    0m0.150s
    sys     0m27.440s
    ~=      38 MB/s

sda7    ->  sdb1
    real    6m32.792s
    user    0m0.010s
    sys     0m6.060s
    ~=      29 MB/s

sdc1    ->  sdb1
    real    6m49.753s
    user    0m0.030s
    sys     0m4.570s
    ~=      28 MB/s

My motherboard is a brand new ASUS P7P55D Pro, which is supposedly a rather good board. All disks (including the external one) are connected to the on-chip connectors.

It looks as if NTFS-3G uses more system resources (and the system does get a bit laggy when transfers are in progress), but the transfer rate is in line with that of the other file system.

What really bugs me is that the larger (and obviously newer) disk appears to be the slowest. Also the general performance seems to be quite a bit worse than I'd expect. Isn't SATA supposed to have a transfer rate of *at least* 150 MB/sec? I get an avarage speed that's about 25% of the minimum speed so I think there must be something wrong.

I'm running Karmic 64 bit, uname -a:

Linux brooke 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 x86_64 GNU/Linux

Any comments/suggestions will be greatly appreciated.

Cheers,
Eros

---

### Post by HappyFeet on 2009-12-09
150mb/sec is a theoretical transfer speed. Those speeds you are getting are in line with what I've seen over the years.

---

