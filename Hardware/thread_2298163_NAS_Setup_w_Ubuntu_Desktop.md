---
title: "NAS Setup w/ Ubuntu Desktop"
date: 2015-10-09
forum: Hardware
---

### Post by jmf421 on 2015-10-09
I am looking to run Ubuntu Desktop on a NAS I built. I am not too good with command line stuff so I prefer this over the Ubuntu Server. 

Currently I have (2) 2TB Hard Drives and was curious to the best setup that can also scale if I were to add an additional hard drive.

Do I install Ubuntu on one of these drives or do you recommend getting a small 64GB SSD to install the OS on? Then I could use the larger drives for storage only. 

Or do I just pool everything together with some type of RAID setup? I am pretty new to all of this and mainly use my NAS for streaming media throughout the house and holding backups from multiple computers.

---

### Post by gordintoronto on 2015-10-09
My preference is to install Xubuntu on a small, old hard drive and use the big drives for the file server. Google fstab for how to mount the other drives at boot time. That way, you don't have to log on to make shared folders available.

---

