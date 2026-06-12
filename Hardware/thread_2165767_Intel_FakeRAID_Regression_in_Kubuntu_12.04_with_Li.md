---
title: "Intel FakeRAID *Regression* in Kubuntu 12.04 with Linux 3.2.0-51"
date: 2013-08-06
forum: Hardware
---

### Post by bmccann on 2013-08-06
I have been using Intel FakeRAID on an Asus Z77 motherboard on Kubuntu 12.04 for months. I'm using the MDADM version and not DMRAID. It has been working fine other than a couple minor issues with clean shutdowns that I fixed by tweaking a couple of the scripts under /etc.

I upgraded to the latest Linux kernel (3.2.0-51) yesterday and my RAID stopped working, probably because auto-detection failed to see the RAID array. 

Here is /proc/mdstat when I run 3.2.0-49:

Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md126 : active raid1 sdb[1] sdc[0]
      976758784 blocks super external:/md127/0 [2/2] [UU]
      
md127 : inactive sdb[1](S) sdc[0](S)
      6306 blocks super external:imsm

The /proc/mdstat file is empty (other than listing personalities) in 3.2.0-51. Note that the sdb and sdc drives are recognized by 3.2.0-51, and their partition tables look reasonable, so I don't see any issues with 3.2.0-51 actually seeing the physical drives. The problem appears to be that the MD driver doesn't detect the external RAID (aka 'imsm') metadata created by Intel fakeraid.


Any suggestions on how to troubleshoot and/or fix this? Should I just file a bug on launchpad.net?

---

