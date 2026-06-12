---
title: "How to handle dualboot system with an NVME disk"
date: 2019-07-26
forum: Hardware
---

### Post by keiyikrutzen on 2019-07-26
Hello,

I'd like some help with the following issue;

we have quite a lot of Dell systems with an M2-Disk (SSD). Dell advices us to put it on raid-on, because Windows doesn't support all AHCI nvmi drivers. If we switch the disk mode to AHCI then Ubuntu actually sees the disk, otherwise it doesn't work. But if we put the disks on AHCI, then it could cause problems when trying to install Windows. The Dell support gave 2 weblinks with possible solutions, but they're not exactly the solution;

[https://www.dell.com/support/article/nl/nl/nldhs1/sln299303/ubuntu-op-systemen-met-pcie-m2-stations-laden?lang=nl](https://www.dell.com/support/article/nl/nl/nldhs1/sln299303/ubuntu-op-systemen-met-pcie-m2-stations-laden?lang=nl)[COLOR=#080707][FONT=&quot][/FONT][/COLOR][https://www.dell.com/support/article/nl/nl/nldhs1/sln308883/het-oplossen-van-een-pcie-nvme-m-2-ssd-ubuntu-kabuntu-installatie-probleem-op-uw-dell-pc?lang=nl](https://www.dell.com/support/article/nl/nl/nldhs1/sln308883/het-oplossen-van-een-pcie-nvme-m-2-ssd-ubuntu-kabuntu-installatie-probleem-op-uw-dell-pc?lang=nl)[COLOR=#080707][FONT=&quot][/FONT][/COLOR]
in conclusion, we'd like some advice on how to run dual boot with Ubuntu and Windows whilst using a NVME Disk

Thanks in advance!

---

### Post by oldfred on 2019-07-26
Intel says there is no difference with their drive.
       Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

Windows uses the Intel RST or RAID for fast start up. So when you turn that off, the fast start up may not work. But you also need to turn fast start up off anyway to dual boot.

[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)

---

