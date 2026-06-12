---
title: "dmraid activating RAID sets problem"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by Saarg on 2005-10-21
I have a motherboard with Intel RAID and Promise Fasttrack 378 built-in.
Installed dmraid via Adept.
dmraid activates my Intel RAID sets and partition at boot so I'm able to mount it through fstab.

The problem is with the Promise RAID sets and partitions. It activates the RAID sets, but not the partitions. After some investigations I found that deactivating the Promise RAID sets and activating them again with "sudo dmraid -ay -v pdc" it detects and activates both the RAID sets and partitions.
I could have just used a script and run it whenever I needed to access the partitions, but I want it to to it at boot time. I tried to edit /etc/init.d/dmraid to make it just activate the Promise devices but that didn't work.

So I wonder if someone could help me getting this working at boot.

---

