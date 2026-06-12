---
title: "wireless question"
date: 2008-11-12
forum: General Help
---

### Post by fouadk on 2008-11-12
hi everyone....

i have installed 8.10 and surprisingly it supports my broadcom wireless card out of the box...but 8.10 was not fully compatible with my laptop(sound and shutdown problems) so i decided to go back to 8.04 until 9.04 is out (hope it will work flawlessly on my laptop) 
my question would be the following, can i make 8.04 use the wireless drivers of 8.10 in some way or another ???

please help

thanks in advance

---

### Post by Ryadt on 2008-11-12
Can you post the output of ```
lshw -C Network
```

---

### Post by fouadk on 2008-11-12
the output is :

PCI (sysfs)  


weird nothing appeard,,, it kept like this for several minutes

---

### Post by Ryadt on 2008-11-12
Try```
lspci
```

---

### Post by fouadk on 2008-11-12
```
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

---

### Post by fouadk on 2008-11-12
ok it got solved...i installed the broadcom in the system/preferences/hardware drivers and it worked,,,,this thing didnt work 6 months ago when hardy was first released,,,,,

very weird....it seems that the ubuntu team got that fixed,,,,

ubuntu rules...

thanks a lot for your time and help...it got fixed by itself

---

### Post by Ryadt on 2008-11-12
The kernel has been upgraded since then and it includes many more wireless drivers in it. ;)

---

### Post by fouadk on 2008-11-12
ok....good but i have some bad news,,,,even though it detected the drivers, the WEP key does not work...i have tried all combinations(128 hex, 128 ascii, 128 passphrase)no success

---

### Post by Ryadt on 2008-11-12
Post the output of```
sudo iwlist scan
```

---

### Post by fouadk on 2008-11-12
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:66:60:FC
                    ESSID:"KADAs"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=85/100  Signal level=-49 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000318d81589
          Cell 02 - Address: 00:1E:58:C5:7A:63
                    ESSID:"Karkosian"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/100  Signal level=-88 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000003f7d9d181

```

---

