---
title: "Iomega Prestige ok with 8.04 finally"
date: 2010-08-19
forum: Hardware
---

### Post by maaark38 on 2010-08-19
I bought a 1TB Iomea Prestige as a backup drive as I am upgrading from Ubuntu Studio 8.04 to 10.04 LTS.  At first it would not work, it did not appear in the list when I did 

*sudo fdisk -l*

I was able to get it to work doing these things:

1 Kept moving the drive from one USB slot to another.  The third try was a charm.  Now it appears as /dev/sdb

2 Ran NTFSFIX and enable writing to the drive

3 The first time I had to manually mount it

[I]mkdir /mnt/IomegHDD
sudo mount -t ntfs-3g /deve/sdb1/media/IomegaHDD -o force
[/I] 

After that it automatically mounts and I can read and write to it.

---

### Post by paulhooker on 2011-08-18
Anybody know if I can make IOMEGA PRESITGE 1TB external hard drive work with UBUNTU 11.04?  There are various threads giving +/- points across LINUX users of IOMEGA, but generally it seemed favourable over other manufacturers.

---

