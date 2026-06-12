---
title: "Ubuntu 11.04 64-bit does not recognize Windows 7 partition"
date: 2011-06-24
forum: Hardware
---

### Post by dopplerdeffect on 2011-06-24
When I try to install Ubuntu 11.04 64-bit, it shows that my entire hard drive is completely empty, even though I have a 300GB partition with Windows 7 (x64) installed and bootable. I had originally installed Ubuntu and tried to get Windows to recognize the partition and it was able to see Linux, but refused to create and install to a bootable partition on the same hard drive. The hard drive is a 2TB Western Digital (WD20EARS).

Any help would be appreciated, I've tried to google but only found cases where Ubuntu showed no free space, not where it showed only free space.

---

### Post by Rubi1200 on 2011-06-25
Hi,
we need some additional information to help you with this one:

1. use a LiveCD and take a screenshot of how GParted sees the drive; post it here

2. run this command from the LiveCD and post the output:
```
sudo fdisk -lu
```

3. check in the Windows Disk Management utility and see whether the disk is reported as Basic or Dynamic; let us know which

4. was the disk ever part of a RAID array to the best of your knowledge?

Thanks.

---

### Post by ergye on 2011-07-12
I had the exact same problem. In my case the the drive was previously GUID partitioned for a Hackintosh setup.

I wiped the drive and installed Win7 and later tried to install Ubuntu but the installer said "This computer currently has no detected operating systems" where in fact it was booting Win7 just fine.

I fixed it by loading the LiveCD and partitioning the drive as ms-dos MBR. Everything installed fine after that.

---

### Post by Signal64 on 2011-07-13
Unfortunately if you get in this situation you have to gptsync the partition table.

[http://manpages.ubuntu.com/manpages/maverick/man8/gptsync.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/gptsync.8.html)

Or start over and re-partition with gparted and a ms-dos MBR as suggested.

---

### Post by oklop on 2011-12-14
I do have the same problem. HDD that I got was a part of RAID before (I got it from a friend). Haven't checked WDM yet, as it's my home comp (I'm currently at work). What can I do regarding RAID HDD history?

---

### Post by Mark Phelps on 2011-12-14
> **oklop said:**
> What can I do regarding RAID HDD history?

What you SHOULD do is, instead of hijacking someone else's thread -- one with a different problem -- is start your own thread, being sure to include RAID in the title.

That way, folks familiar with solving RAID-related problems will see your thread sooner.

---

