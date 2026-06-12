---
title: "Onboard RAID"
date: 2008-05-21
forum: Hardware
---

### Post by thoms1 on 2008-05-21
We have servers with the Intel ESB2 onboard RAID chipset.  We want to set up two drives using RAID 1 (mirroring) using the onboard RAID chipset (some of our developers don't want to use Linux Software RAID).  We also need to be able to check the status of the RAID array and the disks within it via software, so that a drive failure can be reported to the operator.

It appears that Intel's "Matrix Storage Manager" software is Windows only.  There is an Adaptec HostRAID implementation that supports Linux--officially only Red Hat and SuSE, but I'm hoping we can get that working on Ubuntu.

However, I see no tools for Linux that support querying for the status of the RAID array in this situation.  (I know there are tools to do this for Software RAID, and I've seen tools provided by 3ware for their RAID cards, but I haven't seen anything for onboard chipset RAID.)  The scenario I'm most concerned about is detection of the failure of a drive so that the operator knows to replace it and rebuild the array.

I did find a utility called hrconf which at first looked promising, but the "hrconf status" just gives the status of an ongoing command, and some HP literature said that the "hrconf task verify" option wouldn't work if the raid array had failed.  (I guess it just checks that the two drives are in sync or something.)

Does anyone have any other ideas?  Is there an obvious tool I'm not considering?

---

### Post by ASULutzy on 2008-05-21
Just out of curiosity, why are you so set on using a hardware raid over a software one?

I set up a software RAID-1 on the fly (while booted into a running-OS) with mdadm and it works great```
ryan@ryan-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0] sdc1[1]
      112414720 blocks [2/2] [UU]
      
unused devices: <none>
```

---

### Post by thoms1 on 2008-05-21
We've been told to use the onboard RAID controller.  I need to make an effort to figure out how to make it work.  If I can't find a way, that opens up the opportunity to consider other options.  (As stated before, I know that Software RAID or a dedicated Hardware RAID card from a vendor that supports Linux would meet our needs.)

---

### Post by robertlight on 2010-09-16
Did anyone figure out how to use the Intel Matrix ESB2 with Ubuntu?

I'm trying to install Ubuntu 10.04LTS on a MB that has the ESB2 Raid hardware.

I'm hoping someone has found a driver for the Intel ESB2

   - Bob
     light -AT- robertlight.com

---

