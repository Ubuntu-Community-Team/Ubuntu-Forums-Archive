---
title: "Xubuntu 64-bit can't boot into live CD IOMMU"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by metalf8801 on 2008-12-03
I'm trying to install Xubuntu 8.10 64-bit and I'm getting a error message before the live cd even boots 

[ 0.004000]Aperture Beyond 4GB Ignoring
[ 0.004000]Your Bios Memory doesn't leave a aperture memory hole
[ 0.004000]Please enable the IOMMU option in the bios setup
[ 0.004000]This costs you 64mb of ram


so I look around in my BIOS for a while and I can find anything at said IOMMU 


I installed Kubuntu 7.10 64-bit last year without any problems and I have Ubuntu 8.10 32-bit installed right now 

I don't know what info would be helpful so I'm just going to post all the hardware sorry if its over kill 

Foxconn N570SM2AA-8EKRS2H AM2 NVIDIA nForce 570 SLI MCP ATX AMD Motherboard

A-DATA 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)

AMD Athlon X2 4850e 2.5GHz 2 x 512KB L2 Cache Socket AM2 45W Dual-Core Processor

LG 20X DVD±R DVD Burner w/ SecurDisc Tech Black SATA Model GH20NS15

SAMSUNG 20X DVD±R DVD Burner Black SATA Model SH-S203B

Western Digital Caviar SE16 WD2500AAKS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive

Western Digital Caviar GP WD5000AACS 500GB 5400 to 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive

XFX PVT73EYARG GeForce 7300GT 512MB 128-bit GDDR2 PCI Express x16 SLI Supported Video Card

also I found this post but I don't know what its says because its not in English 
[http://ubuntuforum-pt.org/index.php?topic=42710.0](http://ubuntuforum-pt.org/index.php?topic=42710.0)


If anyone could suggest what I should do next that would be great 

Thanks 
Dan

---

### Post by Partyboi2 on 2008-12-03
Have you tried using iommu=soft as a boot option as mentioned [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537")?

---

