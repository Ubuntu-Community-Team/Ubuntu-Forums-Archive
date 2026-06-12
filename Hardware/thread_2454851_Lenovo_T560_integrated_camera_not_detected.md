---
title: "Lenovo T560 integrated camera not detected"
date: 2020-12-07
forum: Hardware
---

### Post by b-kerl on 2020-12-07
Hi,
i've bought a refurbished laptop Lenovo T560. Everything runs fine so far, but chrome is saying, that it's not finding the camera.

In the BIOS it's enabled. I also loaded the setup defaults, to be on the safe side. But lspci 
```

[FONT=monospace][COLOR=#000000]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 08)[/COLOR]
00:02.0 VGA compatible controller: Intel Corporation Skylake GT2 [HD Graphics 520] (rev 07)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #3 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-V (rev 21)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
[/FONT]
```

and lsusb don't show any camera.
```

[FONT=monospace][COLOR=#000000]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/COLOR]
Bus 001 Device 004: ID 8087:0a2b Intel Corp.  
Bus 001 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 002: ID 12d1:15c1 Huawei Technologies Co., Ltd. ME906s LTE M.2 Module
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT]
```

Is there anything i can do to activate the camera? I'm running Kubuntu 20.04.

---

### Post by tonylenovo on 2021-01-04
I am looking for answers in these places:[URL="https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t560/downloads/driver-list/component?name=Camera%20and%20Card%20Reader"]
https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t560/downloads/driver-list/component?name=Camera%20and%20Card%20Reader[/URL] 
[https://lenovo-drivers.com/thinkpad-t560/#CameraandCardReader](https://lenovo-drivers.com/thinkpad-t560/#CameraandCardReader). 
[https://askubuntu.com/questions/461657/integrated-webcam-not-detected-after-update-to-14-04](https://askubuntu.com/questions/461657/integrated-webcam-not-detected-after-update-to-14-04)

---

