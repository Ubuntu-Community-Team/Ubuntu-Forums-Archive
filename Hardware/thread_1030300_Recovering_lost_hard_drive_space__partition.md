---
title: "Recovering lost hard drive space / partition"
date: 2009-01-04
forum: Hardware
---

### Post by fhsm on 2009-01-04
I recently installed 8.10 on my old Thinkpad laptop.  This system came with a small invisible service/recovery partition and a large main NTFS partition.  At some point long ago I upgraded the hard drive.  I can’t remember exactly how I did it (the basic plan was clone and expand).

Using the 8.10 installer to format a new partition I noticed the drive layout was not what I expected.  I had a 110gb NTFS main partition, the 5 gb fat 32 service partition and then a 5 gb raw free space.  My theory is I screwed up the expand step of the upgrade and did it proportionally but the service partition wouldn't play along.

In the install partition step I tried to force ubuntu to use the free space and some of the ntfs space but couldn’t seem to make that happen.  I gave up and just let it just pull from the NTFS partition.  

**Question is**: once the system is done installing how can I recover this space and add it to my ubuntu partition?  It shows up as unallocated in GParted.

Thanks

---

### Post by caljohnsmith on 2009-01-04
How about once you are done with the installation, post the output of:
```
sudo fdisk -lu
```
And please identify your partitions.

---

### Post by fhsm on 2009-01-04
Here is the output:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2efcfff7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   175735034    87867486    7  HPFS/NTFS
/dev/sda2       217909440   225484559     3787560   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3       175735035   217905659    21085312+   5  Extended
/dev/sda5       175735098   216058184    20161543+  83  Linux
/dev/sda6       216058248   217905659      923706   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Interesting that IBM's heavily branded diagnostics partition identifies as Compaq...


sda1 = windows NTFS 
sda2 = fat32 diagnostics partition

sda3 = missing space?

sda5 = ubuntu
sda6 = ubuntu's swap


Thanks for the help.

---

### Post by fhsm on 2009-01-04
I've done a bit more looking into my partions.  I think I got the mapping of my fdisk wrong.  In looking on GParted:

sda1 is clearly the NTFS partition for windows and sda2 is the fat32 IBM service partition.


But it looks like both of ubuntu's partitions are nested under sda3, an "extended partition."
```

>sda3 - extended [20gb]
>>sda5 - ext3 (ubuntu's main partition) [19gb]
>>sda6 - linux-swap (ubuntu's swap partition) [1gb]
```

The lost space labeled unallocated with file system unallocated [4gb].

As far as drive layout sda1 is first, followed by sda3 with its two components (sda5 and sda6), then the unallocated space, and sda2 at the end of the drive.

I just can't seem to make it expand sda5 or 6 into the unallocated space.

---

### Post by caljohnsmith on 2009-01-04
According the output of fdisk, you have only about 2 MB of space between your sda3 extended partition and the sda2 Compaq partition, but you have about 4.5 GB of unused space at the very end of the drive. So unless you were to move the Compaq partition to the end of the drive, then you unfortunately can't add the 4.5 GB to your Ubuntu partitions. If the Compaq partition is supposed to be bootable, I would definitely not recommend moving it, because it is probably just like a normal Windows install in that it will break if you move the starting sector point. But if you don't care about being able to boot that Compaq partition, you could move it to the end of the drive. Or maybe a better option is to simply create another primary partition with that 4.5 GB, and use it for your personal files. Would that maybe work for you?

---

### Post by fhsm on 2009-01-04
Thanks caljohnsmith - that's a great point.  I've never really used this recovery partition.  When the system was new I burned rescue dvds off of it and haven't done anything else with it.

I have however swapped out drives and installed many flavors of linux.  So I just tried to boot into the rescue partition for the first time in years and it blue screened.  

How hard is it to recover a windows partition with a moved starting sector?  

Secondarily it may be a good time to just bank on the DVDs and dump that whole partition.  If I wanted to do so how can I combine the old fat32 recovery partition and the unallocated space with my Ubuntu partition?

---

### Post by caljohnsmith on 2009-01-04
> **fhsm said:**
> Thanks caljohnsmith - that's a great point.  I've never really used this recovery partition.  When the system was new I burned rescue dvds off of it and haven't done anything else with it.

I have however swapped out drives and installed many flavors of linux.  So I just tried to boot into the rescue partition for the first time in years and it blue screened.  

How hard is it to recover a windows partition with a moved starting sector?  

Secondarily it may be a good time to just bank on the DVDs and dump that whole partition.  If I wanted to do so how can I combine the old fat32 recovery partition and the unallocated space with my Ubuntu partition?
My vote is to go with your idea of dumping the whole Compaq partition (since you have it on DVD anyway), and then you can use that space for Ubuntu. So if you decide to do that, and once you delete the sda2 Compaq partition, first resize the sda3 extended partition to extend to the end of the drive; then delete the sda6 swap partition, and create it again at the end of the extended partition, and with the unallocated space in front of it you should be able to enlarge your sda5 Ubuntu partition. Also, when you go to use gparted to do all this, right-click the swap partition and select "swapoff" so that it doesn't prevent you from making your partition changes. Good luck and let me know how it goes. :)

---

### Post by fhsm on 2009-01-06
I ended up using the GParted live CD to unallocate the fat32 partition then shuffled the 9gb raw space down into the extended partition and then expand my Ubuntu partition.

Took a while and a bunch of steps but seems to have worked out.

---

