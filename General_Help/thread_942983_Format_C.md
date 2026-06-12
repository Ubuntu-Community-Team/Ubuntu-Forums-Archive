---
title: "Format C"
date: 2008-10-09
forum: General Help
---

### Post by nohchivusa on 2008-10-09
Hey everyone,

My windows started acting really stupid lately, so I decided to install Ubuntu (I have laptop) as my main OS, without any dual-booting and stuff. I have two disks C and D, so i was wondering if I have to format C? My goal is to get fresh Ubuntu with all my disk spaces (C and D drives are 60 gigs each)

Thanks in advance

---

### Post by SuperSonic4 on 2008-10-09
It depends if they're two partitions of the same drive or two physical drives.

_If they're two partitions on one disk_

Tell ubuntu to use the entire disk, (guided: use entire disk). This will install ubuntu onto the disc erasing all partitions

_If they're two physical drives_

I do not think you can install ubuntu across both but a good solution would be to have essential system and config files on one disc (basically / and /home) and keep media and data on the other (such as media/documents/video etc). You can then edit fstab so that it will mount automatically (it will be /dev/sdb)

---

### Post by oldos2er on 2008-10-09
> **nohchivusa said:**
> 
My windows started acting really stupid lately, so I decided to install Ubuntu (I have laptop) as my main OS, without any dual-booting and stuff. I have two disks C and D, so i was wondering if I have to format C? My goal is to get fresh Ubuntu with all my disk spaces (C and D drives are 60 gigs each)
 

 Just boot from the Ubuntu LiveCD, run the installer, and choose 'Guided--Use Entire Disk' when the option appears.

---

### Post by damis648 on 2008-10-09
> **oldos2er said:**
> just boot from the ubuntu livecd, run the installer, and choose 'guided--use entire disk' when the option appears.

+1

---

### Post by nohchivusa on 2008-10-09
Thanks guys!!!

---

### Post by bodhi.zazen on 2008-10-09
> **nohchivusa said:**
> Hey everyone,

My windows started acting really stupid lately, so I decided to install Ubuntu (I have laptop) as my main OS, without any dual-booting and stuff. I have two disks C and D, so i was wondering if I have to format C? My goal is to get fresh Ubuntu with all my disk spaces (C and D drives are 60 gigs each)

Thanks in advance

Ubuntu does not identify partitions by "C" or "D" or any other letter.

I suggest you start by familiarizing yourself with Linux terminology (so that you do not format the wrong disk / partition).

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

