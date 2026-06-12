---
title: "Slow transfer speeds internal hdd"
date: 2018-03-24
forum: Hardware
---

### Post by Rushed on 2018-03-24
Hi,

I am writing because I noticed that while I transfer files on the same internal HDD, I get slow transfer speeds such as 40MB/s . The HDD is a 4TB WD Green 5400RPM that used to be an external and was transfered into my HTPC.
While it used to be an external drive, i was able to get 120MB/s with it. However, now I get these slow speeds.
I did a test with my SSD and I managed to get 195MB/s so now i'm going towards the HDD being the problem.

Can it be the fact that I transfered from external to internal be the problem?

I ran a dmesg command in terminal and I see that both sata ports are running at 6Gbps..
```
[    1.385108] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.393300] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)

```

Is there a way around this or am I going to be stuck at 40MB/s ?

---

