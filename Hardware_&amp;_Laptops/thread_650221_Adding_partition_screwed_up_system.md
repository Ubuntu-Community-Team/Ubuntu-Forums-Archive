---
title: "Adding partition screwed up system"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by etech1 on 2007-12-26
Hello,
I recently added a 62GB ext3 partition to a hard drive on my Dual boot XP/Gutsy system using gparted. When I booted into Gutsy the drive was listed a 62GB drive and I could mount it as read only. Wanting to use it as regular storage meaning read/write and mount when booting I followed the following instructions but using my drive letters sdd4 instead of hdc1 and my login name

Code:
sudo mkdir /media/hdc1
sudo mount -t ext3 /dev/hdc1 /media/hdc1
df -h
And if you want to write to it, you need to change the ownership of /media/hdc1 from root to your login name. Assuming your login name is juice, do

Code:
sudo chown -R juice:juice /media/hdc1
ls -la /media

After doing this,  ckicking on the 62GB drive folder displays the root drives files instead of an empty drive and won't mount anymore. The RAID array won't mount either and the networking is screwd up saying "aquiring network address" - no internet access. It was connected fine before and the modem works ok in XP.

I'm writing this from my XP system as Ubuntu won't talk to my sat modem so it's difficult to remember exactly what happened. Is there any way to undo what I've done? I would never have tried to add the drive if doing so would screw up the system.

Thanks for any help in this matter.

---

