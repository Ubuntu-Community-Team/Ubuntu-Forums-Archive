---
title: "[SOLVED] Wifi HP dv6721la Intrepid Ibex"
date: 2008-11-30
forum: Hardware
---

### Post by rolodoom on 2008-11-30
Ok, I just installed Intrepid Ibex 32 bits, on my laptop dv6721la. There's no wifi, a only can connect to internet using ethernet. In hardware drivers is listed an activated an Athero's driver, is normal?? how can I connect to the internet using wifi?

---

### Post by sergiom99 on 2008-11-30
please post the output of these commands, typed in a console shell:
lspci
lsusb

Then well find out which card do you have and maybe point you in the right directions.

In the meantime, check this thread to see if it applies to your hardware:
[http://ubuntuforums.org/showthread.php?t=970055](http://ubuntuforums.org/showthread.php?t=970055)

---

### Post by rolodoom on 2008-11-30
```
$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

$lsusb
Bus 004 Device 002: ID 064e:a110 Suyin Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by rolodoom on 2008-11-30
Ok, I'm posting this from my laptop using wifi. Found an answer here:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

I followed the steps as it says:

```
$ sudo update-rc.d -f linux-restricted-modules-common remove
```Then make sure you have Atheros AR242x

```
$ lspci | grep Atheros
```The result is:[INDENT]*05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)*
[/INDENT]```
$ cd ~/Desktop
$ wget -c http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
$ tar xvf compat*.tar.bz2
$ cd compat*
$ sudo apt-get update && sudo apt-get install build-essential
$ make
$ sudo make install
$ sudo make unload
$ sudo make load

```Now reboot

Then you should have wireless, just run:

```
$ iwconfig
```The result should look like this:[INDENT][I]lo        no wireless extensions.

eth6      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SanchezS"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1A:EF:01:7D:1E   
          Bit Rate=5.5 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:Off   Fragment thr=2352 B   
          Power Management:Off
          Link Quality=100/100  Signal level:-39 dBm  Noise level=-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
[/I]
[/INDENT]That&#347; how it worked out for me!!!!

---

