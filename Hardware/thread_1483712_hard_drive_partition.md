---
title: "hard drive partition"
date: 2010-05-14
forum: Hardware
---

### Post by m_ghv_geo on 2010-05-14
[B][SIZE="3"]hi all i have question 
how do i scan in Ubuntu the partition of hard drive for defects i am not looking for complete hard drive scan nor for the Ubuntu file system scan.[/SIZE][/B]

the because i am looking for this is my hard drive is divided by 4 partitions(and first one has a lot of bed sectors) in first one i head win7 and when i was running win7 the hard drive was teking(it was making noses like tik tik), system was freezing randomly(mostly when it was teking) and win7 was giving me errors that files are corrupted,
then i head empty 25gb partition on that same drive and i installed Ubuntu on it but right know i can not open that partition, Ubuntu can not recognize that partition, it is visible in(disk utility) but that all, and right know drive does not making noses and it is working fine except i can not use that partition, but i would like to know if my data on other partitions are safe

sou i need something to check other partitions 
if i use the software which is provided by Samsung(oh i forget my hard drive is from Samsung)it will scan completely whole drive and it will find bad sectors, i already know this drive has bad sectors but i am interesting if there are any bad sectors in partitions sdc5, sdc6 and sdc7

---

### Post by labinnsw on 2010-05-16
Go to System >> Administration >> Disk Utility

On the right, click on the Hard disk where the partition is located

On the left, select the partition you wish to check

Below that, click the "Check Filesystem" Button

---

### Post by m_ghv_geo on 2010-05-16
> **labinnsw said:**
> Go to System >> Administration >> Disk Utility

On the right, click on the Hard disk where the partition is located

On the left, select the partition you wish to check

Below that, click the "Check Filesystem" Button

thx for trying to help. but did you read what i wrote?
i said i am not looking for checking file system, file system check means to check files of Ubuntu O.S itself if they are corrupted or they are ok.
but i need to check hard drive if there are any bed sectors where my sdc5, sdc6 and sdc7 partitions are located,

---

### Post by labinnsw on 2010-05-17
Would that be what the SMART Data button does?
This is on the right, under the heading "Drive" and Above the heading "Benchmark."

---

### Post by m_ghv_geo on 2010-05-17
> **labinnsw said:**
> Would that be what the SMART Data button does?
This is on the right, under the heading "Drive" and Above the heading "Benchmark."

yes it will do but it will not going to give me the information which partition has what problem

**i know this drive has problems but i am interested were are those problems located on my hard drive disc.**

---

### Post by m_ghv_geo on 2010-05-17
i do not understand were are all other Ubuntu users

---

