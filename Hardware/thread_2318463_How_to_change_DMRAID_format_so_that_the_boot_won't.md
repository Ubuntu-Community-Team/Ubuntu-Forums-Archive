---
title: "How to change DMRAID format so that the boot won't hang?"
date: 2016-03-26
forum: Hardware
---

### Post by khh2 on 2016-03-26
Hi,

I have a dual boot computer with an Intel SATA controller where I attach 2 drives on RAID0. It's not a boot partition. I NTFS-formatted the array in Windows.  Everything worked fine.  When I boot into Ubuntu, I had to issue the following command to make it work because DMRAID wrongly used format "ddf1" instead of "isw".

Code:
sudo dmraid -ay -f isw

 The problem is it hangs every time when booting into Ubuntu because of the wrong format.  Is there anyway I can force DMRAID to use format isw at boot time?

---

