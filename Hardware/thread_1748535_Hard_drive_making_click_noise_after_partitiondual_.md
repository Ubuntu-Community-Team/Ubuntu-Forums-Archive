---
title: "Hard drive making click noise after partition/dual boot installation"
date: 2011-05-03
forum: Hardware
---

### Post by caspian915 on 2011-05-03
Hi all,

I just spent the morning reconfiguring my Samsung N145 Netbook to dual boot Windows 7 and the latest stable Natty Narwhal. 

Info:

[B]CPUs: 2
Model Name: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
L2 Cache: 512 KB
RAM: 2GB
HD: 250GB, WDC WD2500BEVT-3[/B]

[B]Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3917    31353856    7  HPFS/NTFS
/dev/sda3            3917        7833    31457280   83  Linux
/dev/sda4            7833       30402   181283840    5  Extended
/dev/sda5            7833       29880   177088512    7  HPFS/NTFS
/dev/sda6           29880       30402     4193280   82  Linux swap / Solaris[/B]


Since I finally finished, I've noticed a clicking noise coming from the hard drive, similar to the sound it makes when it disengages during shutdown, sometimes every few seconds, sometimes only every so often. It only happens in Ubuntu, doesn't seem to happen when I'm booted into Win 7.  

Any suggestions? Is it because of the Partition boundary warning? Do I have too many partitions, or is the Extended partition for data and swap a problem? The netbook is just over a week old, it would be surprising for the hard drive to already be physically damaged.

More info

Formatted and partitioned with GParted Live to 3 partitions for Win 7, Ubuntu, and storage. Loaded Win 7. Then loaded Ubuntu. I followed instructions that said to skip the swap partition and use a swap file on the storage partition. I then did some more research and decided that since I have a limited specs netbook, maybe I should have a swap partition. Created that, (I realize 4GB is a lot, but I had room to spare and might just use hibernation).

---

### Post by caspian915 on 2011-05-03
As a follow-up to this question, I deleted the Extended partition, both the part dedicated to storage and the part that was linux swap and repartitioned as just Primary and NTFS storage (within Gparted Live). I then rebooted into Ubuntu (11.04). Still had the hard drive clicking noise though. 

Even if it's not something to be concerned about, it's still really annoying. Is it possible it's some sort of bug caused by 11.04 not running well on my particular netbook?

---

### Post by fluiz on 2011-08-17
Hi,
I have the some problem with an Acer netbook 722 and dual boot ( Win7 and Ubuntu 11.04)  (I´ve received de Netbook yesterday, so is brand new)  
The HD is also WDC but 500Gb
Did you find any solution.

---

