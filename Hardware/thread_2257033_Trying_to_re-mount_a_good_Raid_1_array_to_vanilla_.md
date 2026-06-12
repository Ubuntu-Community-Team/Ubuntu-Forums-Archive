---
title: "Trying to re-mount a good Raid 1 array to vanilla 14.10 installation"
date: 2014-12-16
forum: Hardware
---

### Post by Eirhead on 2014-12-16
Heya, I have a computer which was previously running a slightly older version of Ubuntu. The O/S was installed on a SSD drive, and it is being used to network share a 2TB raid 1 array. The SSD crapped out really early and needed to be replaced (odd), so I downloaded the latest version of Ubuntu and installed it on the new drive. I don't normally use Ubuntu day-to-day, so please excuse my greenness... and I have done a lot of searching into this problem, but most searches net results that don't really apply to my situation. I absolutely cannot format these drives; and there is nothing wrong with the raid 1 drives. My operating system simply does not access the array yet, but I'm sure it's very simple to have them mounted and working with a little advice from someone a little more familiar with the OS than myself.

When I do a "egrep 'sd[a-z]' /proc/partitions"

the results are 4 different sda entries related to the drive my OS is on, then 1 sdb entry and 1 sdc entry which are my identical raid 1 drives. How should I proceed?

Thanks in advance for your help! =)

---

### Post by Eirhead on 2014-12-16
I got her solved, can't remember what I did, but it works not... too busy tackling other problems now, haahaha

---

