---
title: "Help set up FakeRAID/SoftRAID using mdadm without losing data"
date: 2013-06-26
forum: Hardware
---

### Post by hopungo on 2013-06-26
There is RAID0 of 2 drives connected through Silicon Image 3132 SATA SoftRAID controller. Under Windows it was partitioned as one dynamic GPT-disk having 4 TB NTFS volume. There is a lot of music and movies on the drive. I'm trying to get him to be seen under Ubuntu as a single disk, not as 2 by 2 terabytes.


I tried to read it through dmraid, had no success, it is not displayed in /dev/mapper. Also tried to configure the kernel, but did not find anything suspicious, the driver for my controller was on. There is also a driver from the manufacturer, but it is only available for RHEL and SLES. [Here]("http://www.versalogic.com/kb/KB.asp?KBID=1689") it's reported that SoftRAID is supported by the kernel, but apparently not completely. If I thrust drives in the AMD controller, built into the motherboard, the drive is seen as a single, but the data is lost. I know about mdadm that it is able to ditch all the information on the disks. So, is it possible to somehow create an array without actually recording information on used drives and to make the system correctly identify sections on it later?


Information about the array:
/dev/sdf - Disk 0
/dev/sdg - Disk 1
Array type: Stripe
Block Size: 64KB
Also, a device /dev/md1 is created using command mknod /dev/md1 b 9 1

---

### Post by hopungo on 2013-07-02
Had to destroy my data, but found a solution. The --build option actually constructs an **existing** array and runs it. The full command in my case looks such:
```
sudo mdadm --build --verbose --chunk=64K /dev/md1 --level=0 --raid-devices=2 /dev/sdh /dev/sdi
```
I think that chunk and level options are not necessary, but use them to be sure everything goes right.

---

### Post by rubylaser on 2013-07-02
I love mdadm, but in this case, you would be better off with independent filesystems on each disk.  That way, if you lost one disk, you wouldn't lose everything.  In the future, if you added one more disk, you could easily migrate to [SnapRAID]("http://snapraid.sourceforge.net/") without needing to format your disks, and you can pool them with AUFS of mhddfs very easily.

---

