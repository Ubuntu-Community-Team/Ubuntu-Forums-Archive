---
title: "asus motherboard x399 support"
date: 2017-11-15
forum: Hardware
---

### Post by vitto-m on 2017-11-15
Hi, I've bought this new motherboard for threadripper processors:
asus rog strix x399-e gaming

[https://www.asus.com/us/Motherboards/ROG-STRIX-X399-E-GAMING/specifications/](https://www.asus.com/us/Motherboards/ROG-STRIX-X399-E-GAMING/specifications/)

two questions: 

sensor-detect does not find any thermal sensor. This is weird as on asus bios screen I can see a lot of sensors and their actual temperature. Any way to get those values? 

Second question: the motherboard has a wifi connector 2T2R, but gnome does not find any wifi card. Any way to get it working?

thank you!

here some more infos:

```
System:    Host: ws0 Kernel: 4.10.0-38-generic x86_64 (64 bit gcc: 5.4.0) Desktop: N/A
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: ROG STRIX X399-E GAMING v: Rev 1.xx
           Bios: American Megatrends v: 0402 date: 09/06/2017
CPU:       Hexa core AMD Ryzen Threadripper 1920X 12-Core (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 41918
           clock speeds: max: 3500 MHz 1: 2200 MHz 2: 2200 MHz 3: 2200 MHz 4: 2200 MHz 5: 2200 MHz 6: 2200 MHz
           7: 2200 MHz 8: 2200 MHz 9: 2200 MHz 10: 2200 MHz 11: 2200 MHz 12: 2200 MHz 13: 2200 MHz 14: 2200 MHz
           15: 2200 MHz 16: 2200 MHz 17: 2200 MHz 18: 3500 MHz 19: 2200 MHz 20: 2200 MHz 21: 2200 MHz
           22: 2200 MHz 23: 2200 MHz 24: 2200 MHz
Memory:    No dmidecode memory data: try newer kernel.
Graphics:  Card-1: NVIDIA Device 1b06 bus-ID: 09:00.0
           Card-2: NVIDIA Device 1b06 bus-ID: 41:00.0
           Display Server: X.Org 1.19.3 drivers: nvidia,nouveau (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz, 1366x768@59.79hz
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
Audio:     Card-1 Advanced Micro Devices [AMD] Device 1457 driver: snd_hda_intel bus-ID: 0b:00.3
           Card-2 2x NVIDIA Device 10ef driver: snd_hda_intelsnd_hda_intel bus-ID: 41:00.1
           Sound: Advanced Linux Sound Architecture v: k4.10.0-38-generic
Network:   Card-1: Realtek Device b822 port: 6000 bus-ID: 03:00.0
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
           Card-2: Intel I211 Gigabit Network Connection driver: igb v: 5.4.0-k port: 5000 bus-ID: 05:00.0
           IF: enp5s0 state: up speed: 100 Mbps duplex: full mac: 10:7b:44:92:e1:8b
Drives:    HDD Total Size: 9276.8GB (0.6% used) ID-1: /dev/sda model: ST3000DM008 size: 3000.6GB
           ID-2: /dev/sdb model: ST3000DM008 size: 3000.6GB ID-3: /dev/sdc model: ST3000DM008 size: 3000.6GB
           ID-4: /dev/sdd model: Crucial_CT275MX3 size: 275.1GB
           Optical: No optical drives detected.
Partition: ID-1: / size: 221G used: 25G (12%) fs: ext4 dev: /dev/sdd2
           label: N/A uuid: 14e5b7fe-eeab-4d3e-8863-a43c652e531c
           ID-2: swap-1 size: 34.22GB used: 0.00GB (0%) fs: swap dev: /dev/sdd3
           label: N/A uuid: 5c4b1bbb-73d9-4ff6-89e3-79115d9ffe33
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: N/A mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 1084 Uptime: 2:01 Memory: 5091.8/32094.7MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 


```

---

### Post by Yellow Pasque on 2017-11-15
Do you know what Super I/O chip it uses? It looks like it's hidden under the audio shield, so I can't tell from a screenshot.

AS for the wireless, it would help to know what chipset that is too:
```
sudo update-pciids
lspci
```

---

### Post by paranoidfactoid on 2017-11-24
Hey, a vendor just recommended this same board to me. The Asus STRIX x399-E because I requested wireless and bluetooth. Got here doing a search for compatibility. I'd likely be running UbuntuStudio (preferably 17.10). But I sure don't want to buy this motherboard if it won't support wireless in Linux. OP, is there any way you could follow up on this and determine the wireless chipset?

---

### Post by paranoidfactoid on 2017-11-24
Just to add, this by Steve from Tweaktown 

[https://www.tweaktown.com/guides/8342/amd-x399-tr4-threadripper-motherboard-buyers-guide/index4.html](https://www.tweaktown.com/guides/8342/amd-x399-tr4-threadripper-motherboard-buyers-guide/index4.html)

[> ]("https://www.tweaktown.com/guides/8342/amd-x399-tr4-threadripper-motherboard-buyers-guide/index4.html")[COLOR=#000000][FONT=Roboto]We also find some wireless AC solutions, and the most common so far is the Intel 8265NGW 2x2 (867Mbps) Wireless AC card. We find it built into the motherboard through an M.2 slot wired for WIFI cards and output on the rear IO, and we also find it on an add-in card included with an X399 motherboard. You can take both with you, since both ways it plugs into an M.2 slot wired for WIFI/BT

[/FONT][/COLOR][COLOR=#000000][FONT=Roboto]One vendor has gone above and beyond and implemented a Wireless AD (WiGig) card, the Qualcomm QCA9008, which is capable of up to 4.6Gbps (yea you read that right). The card also supports 2x2 Wireless AC and the other Wireless technologies below it. Wireless AD is super-fast, but it has to have a clear line of sight, and its main use is for future wireless VR headsets. I also spotted an Intel Wireless AC 3168NGW card, but it's half the speed as the other Intel cards I found on other motherboards at 433Mbps (1x1).
[/FONT][/COLOR][COLOR=#000000][FONT=Roboto]
So... either: [/FONT][/COLOR][COLOR=#000000][FONT=Roboto]Intel 8265NGW (most likely), [/FONT][/COLOR][COLOR=#000000][FONT=Roboto]Intel Wireless AC 3168NGW (less likely), or [/FONT][/COLOR][COLOR=#000000][FONT=Roboto]Qualcomm QCA9008 (least likely and will have three antenna ports... this one is on the $500 ASUS Zenith X399 Extreme board, I think. Not the STRIX. [/FONT][/COLOR][COLOR=#000000][FONT=Roboto]
[/FONT][/COLOR]

---

### Post by paranoidfactoid on 2017-11-24
According to this, the 8265 and 3168 are supported in kernels 4.6 and above. 

[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)

And it looks like some linux vendors actually ship Qualcomm QCA9008 boards which suggests that it's supported. But I couldn't find any canonical documentation which says it does. 

But, kernel boot output says it's running 4.10 and the kernel guys say those Intel boards should be supported from 4.6 on up.

---

### Post by paranoidfactoid on 2017-11-24
[http://www.guru3d.com/news-story/asus-shows-rog-strix-x399-e-gaming.html](http://www.guru3d.com/news-story/asus-shows-rog-strix-x399-e-gaming.html)

This review of the strix says the wireless is 2x2, which suggests the Intel 8265:

> [COLOR=#333333][FONT=sans-serif]With so much bandwidth inside the platform, we had to give the X399-E robust connectivity for reaching outside the box. The board&#8217;s Intel Gigabit networking controller delivers a reliable wired link for competitive play, while its 2x2 802.11ac Wi-Fi offers wireless convenience right out of the box. For external devices, USB 3.1 Gen 2 ports provide 10Gbps links in Type-A, Type-C, and front-panel flavors. Add eight USB 3.1 Gen 1 ports, and there&#8217;s enough room for an army of gaming peripherals and VR accessories.[/FONT][/COLOR]

---

### Post by paranoidfactoid on 2017-11-24
Here's an Ubuntu Forum thread on the 8265:

[https://ubuntuforums.org/showthread.php?t=2340679](https://ubuntuforums.org/showthread.php?t=2340679)

Upshot looks like a non-resolution to me. Forum helpers recommended upgrading to a more recent version of Ubuntu. User says the suggestions provided didn't work. He wound up doing a hack to get the card live. And given you're running a recent kernel that supposedly supports this chipset, I'd say that also indicates non-resolution to the underlying problem.

---

### Post by vitto-m on 2017-11-25
nope

---

### Post by vitto-m on 2017-11-25
Hi sorry for the delay.
Here is what i've found:
on linux 4.14 there is some initiall support for wifi card. But On ubuntu 16.04 there are some limitations.
For thermal sensors support there is a kernel module to recompile, but will be integrated in nexte kernel 4.15 with some of others amd improvements.

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) I/O Memory Management Unit
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 59)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric Device 18h Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7
00:19.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0
00:19.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1
00:19.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2
00:19.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3
00:19.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4
00:19.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5
00:19.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric Device 18h Function 6
00:19.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7
01:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43ba (rev 02)
01:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43b6 (rev 02)
01:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b1 (rev 02)
02:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
02:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
02:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
02:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
02:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
02:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b822
05:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
08:00.0 USB controller: ASMedia Technology Inc. Device 2142
09:00.0 VGA compatible controller: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] (rev a1)
09:00.1 Audio device: NVIDIA Corporation GP102 HDMI Audio Controller (rev a1)
0a:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 145a
0a:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Platform Security Processor
0a:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) USB 3.0 Host Controller
0b:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1455
0b:00.2 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
0b:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
40:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Root Complex
40:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) I/O Memory Management Unit
40:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
40:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
40:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
40:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
40:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
40:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
40:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
40:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
40:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
41:00.0 VGA compatible controller: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] (rev a1)
41:00.1 Audio device: NVIDIA Corporation GP102 HDMI Audio Controller (rev a1)
42:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 145a
42:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Platform Security Processor
42:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) USB 3.0 Host Controller
43:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1455
43:00.2 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)

```

---

