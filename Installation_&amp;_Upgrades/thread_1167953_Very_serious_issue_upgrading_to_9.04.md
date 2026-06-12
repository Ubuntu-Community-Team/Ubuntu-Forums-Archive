---
title: "Very serious issue upgrading to 9.04"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by Soldeace on 2009-05-23
Upgrading from Ubuntu 8.10 to 9.04 caused serious problems here. My 1.5TB disk, which was /dev/sdc previously, became /dev/sda after the process and more: it's now mounted as / with all previous content erased. Well, I *think* it's erased, for all of a sudden the 1.5 free TBytes became all filled with only a few MBs free.

I did nothing different from previous Ubuntu upgrades. If anyone shares my problem (and, mostly important, got a solution), please report.


PS: My 80GB HD which had swap in /dev/sdb2 now have it in /dev/sdb1.

---

### Post by taurus on 2009-05-23
Did you use UUID's to mount your partitions in /etc/fstab?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Soldeace on 2009-05-23
> **taurus said:**
> Did you use UUID's to mount your partitions in /etc/fstab?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

No, I keep my fstab UUID-proof (had a few problems with it in the past).

**fdisk**, **blkid** and **df -h** shows exactly the same as I report in my previous post.

Strangely, I boot a Kubuntu live CD and it shows my disks as I've been used to see them (correct /dev/sd<letters>). Now I've just installed Ubuntu 9.04 from scratch and again it assigned wrong letters to my disks.

Everything is running OK now with the former root partition formated and Ubuntu 9.04 reinstalled. Anyway I wonder why it showed my largest HD totally full (I've seen this sort of thing only when I tried to hard copy a partition to another years ago).

PS: I noticed my disks are listed according to capacity (sda the largest with 1.5 TB, sdb with 80 GB, sdc with 40GB and sdd, my USB stick, with 8 GB). Doesn't matter what they had in mind with that, but switching disk assignments is IMHO aggressively abusive and intrusive, mainly because it didn't give me a warning nor an option.

---

### Post by whoop on 2009-05-23
I always remove all unnecessary external devices when installing or upgrading. I think it always helps reducing the amount of mistakes a person/some software can technically make.

---

