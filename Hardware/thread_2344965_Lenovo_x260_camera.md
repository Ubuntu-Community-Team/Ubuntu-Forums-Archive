---
title: "Lenovo x260 camera"
date: 2016-11-29
forum: Hardware
---

### Post by xub78 on 2016-11-29
Hi

I cannot get the integrated web camera on my Lenovo ThinkPad X260, model 20F6007RMN to work.
It is active in the bios and the bios is upgraded to the latest available (1.23)

Running Xubuntu 16.10 (upgraded from 16.04)

```
lswh -short:
H/W path       Device         Class          Description
========================================================
                              system         20F6007RMN (LENOVO_MT_20F6_BU_Think_FM_ThinkPad X260)
/0                            bus            20F6007RMN
/0/3                          memory         64KiB L1 cache
/0/4                          memory         64KiB L1 cache
/0/5                          memory         512KiB L2 cache
/0/6                          memory         4MiB L3 cache
/0/7                          processor      Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
/0/8                          memory         16GiB System Memory
/0/8/0                        memory         16GiB Chip DDR4 Synchronous 2133 MHz (0,5 ns)
/0/8/1                        memory         SODIMM [empty]
/0/c                          memory         128KiB BIOS
/0/100                        bridge         Skylake Host Bridge/DRAM Registers
/0/100/2                      display        HD Graphics 520
/0/100/14                     bus            Sunrise Point-LP USB 3.0 xHCI Controller
/0/100/14/0    usb1           bus            xHCI Host Controller
/0/100/14/0/3                 communication  HUAWEI Mobile
/0/100/14/0/5                 generic        EMV Smartcard Reader
/0/100/14/0/7                 communication  Bluetooth wireless interface
/0/100/14/1    usb2           bus            xHCI Host Controller
/0/100/14.2                   generic        Sunrise Point-LP Thermal subsystem
/0/100/16                     communication  Sunrise Point-LP CSME HECI #1
/0/100/17                     storage        Sunrise Point-LP SATA Controller [AHCI mode]
/0/100/1c                     bridge         Intel Corporation
/0/100/1c/0                   generic        RTS522A PCI Express Card Reader
/0/100/1c.2                   bridge         Intel Corporation
/0/100/1c.2/0  wlp4s0         network        Wireless 8260
/0/100/1f                     bridge         Sunrise Point-LP LPC Controller
/0/100/1f.2                   memory         Memory controller
/0/100/1f.3                   multimedia     Sunrise Point-LP HD Audio
/0/100/1f.4                   bus            Sunrise Point-LP SMBus
/0/100/1f.6    enp0s31f6      network        Ethernet Connection I219-V
/0/0           scsi1          storage        
/0/0/0.0.0     /dev/sda       disk           512GB SAMSUNG MZ7LN512
/0/0/0.0.0/1                  volume         511MiB Windows FAT volume
/0/0/0.0.0/2   /dev/sda2      volume         460GiB EXT4 volume
/0/0/0.0.0/3   /dev/sda3      volume         15GiB Linux swap volume
/1                            power          45N1773
/2                            power          45N1775
/3             enp0s20f0u3c2  network        Ethernet interface




```


```
lspci
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Device 9d12 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-V (rev 21)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)



```

```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 002: ID 12d1:15c1 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```


I am not even sure the camera is turned on, but there is no Fn-combination that controls it... thanks!

---

