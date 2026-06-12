---
title: "SD Card Reader not working (Thinkpad L560 / PCI device??)"
date: 2018-02-04
forum: Hardware
---

### Post by gde061-www on 2018-02-04
I can't get my ubuntu system to mount my SD card.  
  So far I have tried: ```
sudo apt-get install --reinstall udisks2
```
  I have also tried:   ```
sudo apt-get install exfat-utils exfat-fuse
```
  These did nothing.  The machine is a ThinkPad L560 20f2.  I don't  know what to look for with lsusb or lspci.  There is something called  "SD host controller" at  This issue comes up enough in forums... seems  like a major problem with drivers. 
  Output of >>LSUSB
   ```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 003: ID 8087:0a2b Intel Corp.  
Bus 001 Device 002: ID 04ca:7058 Lite-On Technology Corp.  
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub`
``` 
  Output of >>lspci
   ```
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08) 
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07) 
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model 
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21) 
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21) 
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21) 
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21) 
00:1c.0 PCI bridge: Intel Corporation Device 9d13 (rev f1) 
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1) 
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1) 
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21) 
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21) 
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21) 
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21) 
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-V (rev 21) 
02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a) 
05:00.0 SD Host controller: O2 Micro, Inc. Device 8621 (rev 01) 

>>lspci -v -s 05:00.0
   05:00.0 SD Host controller: O2 Micro, Inc. Device 8621 (rev 01) (prog-if 01)     
Subsystem: Lenovo Device 222c     
Flags: bus master, fast devsel, latency 0, 
IRQ 16     
Memory at e2401000 (32-bit, non-prefetchable) [size=4K]     
Memory at e2400000 (32-bit, non-prefetchable) [size=2K] 
    Capabilities:      <access denied>
Kernel driver in use: sdhci-pci     
Kernel modules: sdhci_pci 
```

  And output of >>sudo parted -l
```

Model: ATA WDC WD5000LPLX-0 (scsi) 
Disk /dev/sda:  500GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: msdos 
Disk  Flags:  
Number  Start   End     Size    Type     File system     Flags  
1      1049kB  3185MB  3183MB  primary  ntfs            boot  
2      3185MB  238GB   235GB   primary  ntfs  
3      238GB   482GB   244GB   primary  ext4  
4      482GB   500GB   18.0GB  primary  linux-swap(v1) 
```

  Finally, output of lsblk  
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
 sda      8:0    0 465.8G  0 disk
  &#9500;&#9472;sda1   8:1    0     3G  0 part
  &#9500;&#9472;sda2   8:2    0 218.9G  0 part
  &#9500;&#9472;sda3   8:3    0 227.1G  0 part /
 &#9492;&#9472;sda4   8:4    0  16.8G  0 part
 [SWAP] sr0     11:0    1  1024M  0 rom
```
 
Seems like the device is on Pci 5, but nothing shows up in block storage that I can mount.  Please help!

---

### Post by linuchsan on 2018-02-04
[https://github.com/Zibri/Realtek-rts5229-linux-driver](https://github.com/Zibri/Realtek-rts5229-linux-driver)

---

