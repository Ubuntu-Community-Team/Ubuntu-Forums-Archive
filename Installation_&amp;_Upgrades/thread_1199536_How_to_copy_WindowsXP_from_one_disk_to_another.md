---
title: "How to copy WindowsXP from one disk to another?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by eckz59 on 2009-06-29
Hi guys,

I've been here before and I know you all are very helpful, so I thought I'd post this here.

I've got a 40GB Seagate hard drive with Windows XP (NTFS partition) that has recently filled up and I'd like to make a copy of this partition on my Raptor 74GB hard drive.

Using GParted to copy the NTFS partition onto the Raptor disk, followed by setting the boot flag, and copying the MBR with dd (bs=512 count=1) didn't work as expected... I tried unplugging the 40GB drive and just letting BIOS boot from the Raptor, but I received an error about reading the disk. I think this probably is caused by either the MBR on the Raptor not matching the disk contents/locations or something.

Can someone please explain how I can copy my "Windows" disk (/dev/sdb) onto my larger, physically different Raptor(/dev/sda)? I want to be able to just boot from the Raptor drive and go, with the ability to expand the partition to take advantage of the extra 30+ GB of unusued space.

Thanks for your help, this has had me very confused for a while now.

---

### Post by dmizer on 2009-06-29
I suggest this tool: [http://www.miray.de/products/sat.hdclone.html](http://www.miray.de/products/sat.hdclone.html)

---

