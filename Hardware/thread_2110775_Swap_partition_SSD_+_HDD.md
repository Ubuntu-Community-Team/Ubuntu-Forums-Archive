---
title: "Swap partition SSD + HDD"
date: 2013-01-31
forum: Hardware
---

### Post by tonycarreira on 2013-01-31
Hi guys,

I have a SSD and a HDD drive. Obviously the SSD drive is small (only 100GB) and the HDD is bigger (2TB). I am having some instability after installing (system just freezes at random) and I was wondering if it is because I have the main system installed in the SSD and the SWAP partition in the HDD... Did I do a mess up by installing the SWAP space in the HDD whilst having the system installed in the SSD ?

Many thanks in advance!

---

### Post by tgalati4 on 2013-01-31
Open a terminal, and keep it open:

```
free
```

You will see a line with Swap:

tgalati4@Dell600m-mint14 ~/Desktop $ free
             total       used       free     shared    buffers     cached
Mem:       2065156    1043372    1021784          0     125088     464860
-/+ buffers/cache:     453424    1611732
Swap:      1914876          0    1914876

As long as "Used" remains 0, then swap isn't being used, and if your freeze occurs and swap was still 0, then something else is causing the issue.  Was is the make and model of SSD?  Some are better than others.  Perhaps yours is faulty?

---

