---
title: "mp4 partition lost!"
date: 2010-12-31
forum: Hardware
---

### Post by zeolite on 2010-12-31
Hi all,
I tried to use my mp4 as a boot disk for install Ubuntu on my new netbook, however, I followed a method on a webside use fdisk or some other commands to format my mp4.

The original size of my mp4 is 16G, however, when I plug it to a computer now, it only shows 10M!!! That is so frustrating~

I think there must be something wrong with the mp4.

I am really new for Ubuntu, so I tried some commands followed by some websites, and the results are as follows:

sudo fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 10 MB, 10469376 bytes
1 heads, 20 sectors/track, 1022 cylinders
Units = cylinders of 20 * 512 = 10240 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

----------------------------------------------------------------------------
Command (m for help): v
Remaining 20447 unallocated 512-byte sectors
----------------------------------------------------------------------------

I wish someone can help me.

Thanks in advance!

May all a happy new year!

---

### Post by IcarusR on 2010-12-31
Use gparted to check the mp4 partitions. I guess you created a partition of 10mb only & the rest is unused space.

Post link to instructions you used.

---

### Post by zeolite on 2010-12-31
> **IcarusR said:**
> Use gparted to check the mp4 partitions. I guess you created a partition of 10mb only & the rest is unused space.

Post link to instructions you used.

Hi IcarusR,
Thank you for your reply.

Because I am a fresh man in linux, and I asked someone help me to do the following:
[http://wiki.centos.org/HowTos/InstallFromUSBkey](http://wiki.centos.org/HowTos/InstallFromUSBkey)

and then I used fdisk, but I don't remember what I have done to it~

I tried to use gparted, and all it shows 10mb unused space. That means the rest space is not detected.

Happy new years!
[IMG]http://ubuntuforums.org/home/jhuang/snapshot1.png[/IMG]

---

### Post by IcarusR on 2011-01-01
If you are trying to get the ubuntu install cd image onto this item I would suggest you start again & use unetbootin. 
This is available in linux or windows format & will download (or you can point it to an iso image) & install the install iso image to your usb drive. 
This is a much simpler way, no partitioning needed as it does it all for you.

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by zeolite on 2011-01-01
> **IcarusR said:**
> If you are trying to get the ubuntu install cd image onto this item I would suggest you start again & use unetbootin. 
This is available in linux or windows format & will download (or you can point it to an iso image) & install the install iso image to your usb drive. 
This is a much simpler way, no partitioning needed as it does it all for you.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Thanks.

The problem is that my mp4 has lost its partition, and I want to find the space back. It was 16G for the mp4, but now it is only 10M.

regards,

---

### Post by zeolite on 2011-01-02
Anyone can help me?

Thanks.

---

### Post by oldfred on 2011-01-02
Testdisk may let you recover it. Does gparted not see the empty space? The CHS value of 1 head looks strange, as CHS values are not used with LBA? Something is not correct with drive.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by logangorence on 2011-01-02
Use System -> Administration -> Disk Utility and Find your MP4 and format it that way. Use FAT drive format and give it a label. Your MP4 will now work with Windows computer too.

---

### Post by zeolite on 2011-01-03
> **oldfred said:**
> Testdisk may let you recover it. Does gparted not see the empty space? The CHS value of 1 head looks strange, as CHS values are not used with LBA? Something is not correct with drive.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Hi, I tried testdisk with the links you provided. However, the situation mentioned in the links are different from mine. In addition, when I use fdisk, it still shows 10M (which should be 16G). Gparted does not see the empty space, and it just show 10M. I am totally confused~

Thanks for your reply.

---

### Post by zeolite on 2011-01-03
> **logangorence said:**
> Use System -> Administration -> Disk Utility and Find your MP4 and format it that way. Use FAT drive format and give it a label. Your MP4 will now work with Windows computer too.

Hi,
It still shows 10M after format as you mentioned~

Thank you for your help.

---

