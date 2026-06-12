---
title: "hdparm -t /dev/sda EXTREMELY low"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by numeritos on 2007-09-11
Hey guys! I bought a new PC and installed kubuntu on it. Everything is running smoothly but I'm not getting the performance I thought I would have. I bought the following:

Core2Duo 4400 2Ghz FSB 800Mhz 2MB
2GB DDR2 800Mhz OCZ SystemElite
320GB SATAII 16MB Samsung
Nvidia 7600GT 256MB
Mother MSI P35 Neo-F


I started noticing low performance when using VM or decompressing tar.gz's. I started being suspicious with my harddrive, so I made the typical hdparm test. It showed me a very poor performance:
```
# hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:   12 MB in  3.13 seconds =   3.83 MB/sec
```

But when it reads from cache it seems ok:
```
# hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   2564 MB in  2.00 seconds = 1281.99 MB/sec
root@kubuntu:/home/numeritos# hdparm -t /dev/sda
```

Could it be a driver problem?

---

### Post by drpaul on 2007-09-11
I ran the test on my notebook with the following results

l:~$ sudo hdparm -t /dev/sda
Password:

/dev/sda:
 Timing buffered disk reads:  120 MB in  3.03 seconds =  39.59 MB/sec
paul@hppaul:~$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   3900 MB in  2.00 seconds = 1950.18 MB/sec

Similar cache results but 10x better buffered.

Running uptodate Edgy on a HP dv6150 [?]. SATA drive. You could have a HD problem.
Have you run HD diagnostics?

HTH

Paul

---

### Post by numeritos on 2007-09-11
> **drpaul said:**
> I ran the test on my notebook with the following results

l:~$ sudo hdparm -t /dev/sda
Password:

/dev/sda:
 Timing buffered disk reads:  120 MB in  3.03 seconds =  39.59 MB/sec
paul@hppaul:~$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   3900 MB in  2.00 seconds = 1950.18 MB/sec

Similar cache results but 10x better buffered.

Running uptodate Edgy on a HP dv6150 [?]. SATA drive. You could have a HD problem.
Have you run HD diagnostics?

HTH

Paul
No, I haven't. Should I run fsck? It doesn't seem a hardware problem to me

---

### Post by numeritos on 2007-09-11
Well, I finally found was the problem was!

At boot, I used the kernel boot option "generic.all_generic_ide" because if I didn't my IDEs CD-RW and DVD-RW weren't detected. The problem was that my HD used those drivers too! After I removed that option the times came back to normal

```
# hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  228 MB in  3.01 seconds =  75.63 MB/sec
```

But now the problem is I don't have any IDE drive...

---

