---
title: "No sound on Samsung CF791"
date: 2019-06-10
forum: Hardware
---

### Post by cristofaro2 on 2019-06-10
Hello,
 I have two external monitor connected via a Dell TB16 (thunderbolt).
One is a Samsung T28C570 and the other one is a Samsung CF791.
The first one is connected via HDMI. The second one is connected via Display Port.
 The problem is that sound on Samsung CF791 doesn't work.
 
I know it's not a mixer problem because:

1) Sometime, If i press CTRL+ALT+F2 (to enter in console mode) and then  go back on Desktop with CTRL+ALT+F1 i can heard sound from the monitor  when I increase or decrease volume, even if a little bit distorted.  Nevertheless, if I try to play a video (for example youtube), sound  stops to work. I have to stop any audio stream, return to console mode  and back again in desktop to hear again distorted sound then increase  volume.
2) On Windows, I have no problem (so it seems not to be an hardware issue).
 
I tried to connect the CF791 via HDMI, but problem persist.
I have no problem with the other monitor.
 I have checked every alsamixer e pavucontrol settings unsuccessful.


 My laptop is a Dell XPS 13.

 Description:    Ubuntu 18.04.2 LTS
Release:        18.04

 
THe HDMI2 is the not working audio device:

 ```
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: PCH [HDA Intel PCH], dispositivo 0: ALC3271 Analog [ALC3271 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 9: HDMI 3 [HDMI 3]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 10: HDMI 4 [HDMI 4]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Dock [WD15 Dock], dispositivo 0: USB Audio [USB Audio]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Dock [WD15 Dock], dispositivo 1: USB Audio [USB Audio #1]
  Sottoperiferiche: 1/1

 
```

Hardware list:
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200  v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #3 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
03:00.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:00.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:01.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:02.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
04:04.0 PCI bridge: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] (rev 02)
05:00.0 System peripheral: Intel Corporation JHL6540 Thunderbolt 3 NHI (C step) [Alpine Ridge 4C 2016] (rev 02)
3a:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
3b:01.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
3b:04.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
3d:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
3e:01.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
3e:04.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
3f:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
6e:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 0116

 
```

lsusb:

```
Bus 004 Device 003: ID 0bda:8153 Realtek Semiconductor Corp.
Bus 004 Device 002: ID 0424:5807 Standard Microsystems Corp.
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:4014 Realtek Semiconductor Corp.
Bus 003 Device 002: ID 0424:2807 Standard Microsystems Corp.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:e0a2 Foxconn / Hon Hai
Bus 001 Device 002: ID 0bda:58f4 Realtek Semiconductor Corp.
Bus 001 Device 004: ID 27c6:5385
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 
```

Best regards,
Salvatore

---

