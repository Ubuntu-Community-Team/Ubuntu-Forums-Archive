---
title: "Am I losing anything if I change from Intel RST to AHCI?"
date: 2019-12-26
forum: Hardware
---

### Post by meiselstein on 2019-12-26
I have an Asus Vivobook 15. In order to install Ubuntu, I have to change the SATA configuration in BIOS from Intel RST with Intel Optane Memory to AHCI. Otherwise, the HD is not recognized during installation.

I am basically a computer newb and I was just wondering if I am losing anything significant by switching to AHCI. I read some articles online that said Optane is faster and saves battery. However, I only have one SSD on my laptop (which I read kind of defeats the purpose of the Intel RST).

---

### Post by Dennis N on 2019-12-26
Intel Optane is not supported in Linux; it only works on Windows 10 64 bit.

---

### Post by oldfred on 2019-12-26
If using an SSD, I do not know if Optane adds anything.

       Intel RST
[https://www.intel.com/content/www/us/en/architecture-and-technology/rapid-storage-technology.html](https://www.intel.com/content/www/us/en/architecture-and-technology/rapid-storage-technology.html)
Optane Memory Module - Frequently Asked Questions 
[https://www.dell.com/support/article/us/en/04/sln306745/optane-memory-module-frequently-asked-questions?lang=en](https://www.dell.com/support/article/us/en/04/sln306745/optane-memory-module-frequently-asked-questions?lang=en)
Optane enabled system may not boot when a Hard Drive or Optane device fails 
[URL="https://www.dell.com/support/article/us/en/04/sln306541/optane-enabled-system-may-not-boot-when-a-hard-drive-or-optane-device-fails?lang=en"]https://www.dell.com/support/article/us/en/04/sln306541/optane-enabled-system-may-not-boot-when-a-hard-drive-or-optane-device-fails?lang=en
      [/URL]
 AHCI vs RAID speed same, one user says power use lower with RAID?
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://itpeernetwork.intel.com/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi/](https://itpeernetwork.intel.com/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi/) 
    [URL="https://www.dell.com/support/article/us/en/04/sln306541/optane-enabled-system-may-not-boot-when-a-hard-drive-or-optane-device-fails?lang=en"]
[/URL]

---

