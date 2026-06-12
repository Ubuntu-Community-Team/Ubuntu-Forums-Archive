---
title: "RAID5 Storage Not Reading Properly in Ubuntu 20.4.02"
date: 2021-08-22
forum: Hardware
---

### Post by wileymiester on 2021-08-22
Howdy!

I have a RAID5 storage setup and just got a notification that one of the HDDs has gone bad.  I plugged the RAID into my windows PC to diagnose (I can't get the QNAP utility to run in Ubuntu) and confirmed the issue, swapped the bad hdd, and had it start rebuilding itself.  When I plugged it back into Ubuntu, gparted says the 'primary gpt table is corrupt but the backup appears ok sot that will be used' and is showing me the attached...

The drive is formatted in exFAT which had been working fine before this.  When I plug it back into windows it reads fine.  Not sure how to get Ubuntu to read this properly without losing my data as it looks like it wants me to repartition the whole thing.

I tried just popping in a flash drive that was formatted in exFAT and that reads ok.

Any suggestions would be appreciated.

---

