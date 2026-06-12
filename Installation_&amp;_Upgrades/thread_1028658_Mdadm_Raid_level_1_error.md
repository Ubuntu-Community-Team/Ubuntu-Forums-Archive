---
title: "Mdadm Raid level 1 error"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by pmdw on 2009-01-02
Hi 
I am try in to setup a raid level 1 on two hdd

I know that both disks work as I can format and fill them with files and compare etc..  and all is working

The thing is I had these drives working as a raid under Red Hat 7 but due to a network issue decided to upgrade to ubuntu.

When I try to set it up I get this.
How do I trouble shoot this?

peter@LinuxBox:~$ sudo mdadm --detail /dev/md0
[sudo] password for peter:
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Jan  2 20:15:34 2009
     Raid Level : raid1
     Array Size : 19550976 (18.65 GiB 20.02 GB)
  Used Dev Size : 19550976 (18.65 GiB 20.02 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jan  2 20:16:26 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           UUID : 42b249d1:8b2c5c20:2ae38843:adf23e8c (local to host LinuxBox)
         Events : 0.13

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       8       17        -      faulty spare   /dev/sdb1

I get the above result after I have run this
sudo mdadm --create /dev/md0 --level=1 --verbose --raid-devices=2 /dev/sdb1 /dev/sdc1   

When I call the --detail I get also get 
 Rebuild Status : 0% complete
and this goes up to 2 % and then errors out.

I am pretty sure of the hardware as it was all working ok before
and I have not made any changes except where the network cable is plugged in.

Questions :confused:
1. How do I trouble shoot this? ( what Log files am I looking for here)
2. Do I need to run mkfs on each partition before I do the create?
2a. or just on the md0 after I get things working?

3. Is there a better option under ubuntu to make a raid with?

Thanks 
Peter

---

