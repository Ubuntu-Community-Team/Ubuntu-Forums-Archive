---
title: "External hard-drive filesystem format"
date: 2009-09-24
forum: Hardware
---

### Post by FFighter on 2009-09-24
Hello forum!

I just bought a SignatureMini external portable hard-drive 250GB, which works great so far. 

I have been happily been using it until the idea to check its filesystem format popped into my head, and my inner-geek came into action, along with concerns of the "I might not be using it in the most optimal way" nature.

I don't know which filesystem it came formatted in, and I don't know how to check. I tried "fdisk -l" and it gave me the following kind of cryptic info:

> arcelo@marcelo-laptop:/dev$ sudo fdisk -l /dev/sdb1
[sudo] password for marcelo: 

Disk /dev/sdb1: 250.0 GB, 250056705024 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.
 

It seems the device has 4 partitions, but when mounted, the I only see one (labeled SignatureMini). Also, the "System" column shows Unknown / Novell Netware / Empty values respectively. Besides that, it shows the message "Partition n doesn'not end on cylinder boundary" -- not sure what this really means, and if it is something bad.

My concern is that I might be using the drive with a filesystem that is not optimal / very compatible with Linux, and that I might be loosing space in the drive because of it. 

Also, of course, my curiosity is huge, and I really like to be aware of what filesystem it is using and why it shows 4 partitions when I ask for information about it through fdisk. 

I would format it now to use Ext4, but it already has lots of data, so, it is a tough decision, since it is working fine.

Anyway, if someone could enlighten-me here, I would be really grateful!

---

### Post by scouser73 on 2009-09-24
Install Gparted which is in the repositories and you will be able to see the filesystem format from there.  Once you have installed Gparted you will find it under **System > Administration > Partition Editor**

---

