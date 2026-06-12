---
title: "Ubuntu 18.4 NVME Disk issues"
date: 2019-08-01
forum: Hardware
---

### Post by keiyikrutzen on 2019-08-01
Hello all,

I posted a topic a few days ago, but now the issue is more clear.

Our customer has been using Dual boot on Dell systems. They use NVME disks and Raid-on. This always worked, until version 18.4. Now Dell recommends using AHCI instead of Raid-on. However, this is a very impactful change for the customer, considering all their systems run on Raid-on. Dell only supports Ubuntu 18.4 with SSD's and Dual Boot right now. The support for NVME Disks stops at version 16.4. 

Now, I understand that this is an issue that isn't limited to Dell but now the customer is just changing config every time.

15.4 was AHCI, 16.4 was Raid-on, now we're back to AHCI with 18.4.

The customer is using kernel 4.15, by the way. 

Am I correct in saying that Raid-on with Dual Boot just doesn't work at the moment for 18.4?

---

### Post by oldfred on 2019-08-01
Except possibly for server installs, I have never seen a desktop of any version work with RAID on.
Since 12.04 and its Alternative installer which included RAID drivers did RAID work for desktop. Only recent versions would even see the RAID, but grub will not install with Desktop installer.

I think all Dell is saying is that you do not use Dell drivers, but either Windows & Linux NVMe drivers.

Generally Dell needs UEFI update & SSD firmware update.
       [https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) 
    
Windows requires you to install AHCI drivers so you do not have to switch.
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
       Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

---

