---
title: "How do I enable touchscreen support on my laptop?"
date: 2023-05-30
forum: Hardware
---

### Post by eddeemn on 2023-05-30
I am unable to use the touchscreen on my new laptop in Ubuntu. My old Pavilion laptop had a touchscreen that worked perfectly in Ubuntu but this new one (HP Pavilion Laptop PC 15-eg2000) doesn't. It has not worked since I got the laptop in February so the recent change to 23.04 isn't something that made it suddenly stop working.



Partial output of **hostnamectl**
    
        ```

    Operating System: Ubuntu 23.04                              Kernel: Linux 6.2.0-20-generic
    Architecture: x86-64
 Hardware Vendor: HP
  Hardware Model: HP Pavilion Laptop 15t-eg200
Firmware Version: F.12

```



Output of **lspci**

```
00:00.0 Host bridge: Intel Corporation Device 4601 (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Alder Lake-UP3 GT2 [Iris Xe Graphics] (rev 0c)
00:04.0 Signal processing controller: Intel Corporation Alder Lake Innovation Platform Framework Processor Participant (rev 04)
00:08.0 System peripheral: Intel Corporation 12th Gen Core Processor Gaussian & Neural Accelerator (rev 04)
00:0d.0 USB controller: Intel Corporation Alder Lake-P Thunderbolt 4 USB Controller (rev 04)
00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01)
00:15.1 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #1 (rev 01)
00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation Alder Lake PCH-P PCI Express Root Port #9 (rev 01)
00:1d.0 PCI bridge: Intel Corporation Device 51b0 (rev 01)
00:1f.0 ISA bridge: Intel Corporation Alder Lake PCH eSPI Controller (rev 01)
00:1f.3 Multimedia audio controller: Intel Corporation Alder Lake PCH-P High Definition Audio Controller (rev 01)
00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
01:00.0 Network controller: MEDIATEK Corp. MT7921 802.11ax PCI Express Wireless Network Adapter
02:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. Device 5017 (rev 03)
```


Output of **lsusb**

```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f3:0c00 Elan Microelectronics Corp. ELAN:ARM-M4
Bus 003 Device 002: ID 30c9:0065 Luxvisions Innotech Limited HP Wide Vision HD Camera
Bus 003 Device 004: ID 13d3:3567 IMC Networks Wireless_Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

