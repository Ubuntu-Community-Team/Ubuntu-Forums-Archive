---
title: "Questions on Installing Ubuntu on Thinkpad X200!"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by huruixd on 2009-02-04
Hi friends,

I just bought a Lenovo Thinkpad X200 with Windows Vista Business pre-installed, I am planning to install Ubuntu(8.04/8.10) on it to get a dual boot systems.

This laptop is brand new, so far, it has only three disk partitions:
   (a) C disk (137GB)  -- where Vista is installed
   (b) Lenovo Q (back up files) (11GB) --  I don't know what it is for.
   (c) ThinkVantage (1.5GB)--  looks like for rescue and recovery
I would like to divid the whole hard drive (160GB) as follows:
   56GB for Ubuntu (Home Director 40GB + System 12GB + Swap Area 4GB)
   81GB for Vista (C disk 30GB + D disk 30GB + E disk 21GB)
   11GB for Lenovo Q -- leave it like it is
   1.5GB for ThinkVatage  -- leave it like it is

My question is:
1.  I am wondering if the 12GB disk space is large enough for installing Ubuntu system. Does anyone have better suggestions?

2. Should I partition the hard drive first or should I install Ubuntu first?

3. Before I started intallation, I would like to back up the vista system in case it goes corrupt during the installation. Since there is no optical drive in X200, could I back up the vista in a external hard drive or burn it into a DVD?

4. What should I do if I want to maintain the function of the ThinkVantage Button --  One Button Recovery



Thank you.

---

### Post by avtolle on 2009-02-04
As to 1: 12 gb should be more than sufficient for system.
As to 2: Use the Vista tool to shrink its partition before installing. Defrag (yes, I know your system is very new) to leave unallocated space for the Ubuntu install, then select manual partitioning; you would need to make an Extended partition as I see it within which to install the system, your home and swap. Remember to format the partitions for Ubuntu system, etc., to Ext3, and to assign / as the mount point for the system; /home for home; and /for swap.
As to 3: Yes, back it up in either way; do a system restore backup, imho, to DVDs at the very least.
As to 4: Don't know the answer to that, but if that partition is not disturbed, I would hope that it would or could be found in the manner you desire.

Good luck, and post back with questions.

---

### Post by aliensun on 2009-05-14
Hi huruixd,

Thanks for sharing. I just bought my x200 as well and would like to do exactly the same thing as you did. However, I can't use the vista disk space shrinking tools even I after I did the defrag. I wonder if it is save to use ubuntu's tool to shrink the disk before installation?

Thanks,
aliensun

---

