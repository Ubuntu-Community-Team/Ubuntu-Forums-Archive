---
title: "BUG: The problem with the laptop lid closed when the monitor is connected"
date: 2013-05-07
forum: Hardware
---

### Post by fallout4all on 2013-05-07
The problem with the laptop lid closed when the monitor is connected. When i close laptop lid, secondary monitor(CRT) is turn off, but if i move mouse monitor is on(laptop monitor and secondary in mirror mode, and i change parametrs dconf>org>gnome>settings daemon>plugins>power : "Laptop lid close action when on AC" and "Laptop lid close action on battery" to "do nothing" and this is not help to prevent switch off of external monitor)...then i start video player(totem or VLC or Smplayer) and start to watch video and see a lags(1 sec freezes) in video. When i open the laptop lid (both monitors start reconfigure) and video has no lags.




OS ubuntu 13.04 x32_64(clean install) Installed Bumblebee because optimus nvidia. Installed vaapi intel driver for mplayer and other codecs


My laptop configure is Core&#8482; i3-2310M + Nvidia GeForce 540m + 8GB RAM


```
lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev ff)

```
```
lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev ff)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
0d:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)

```

PS: I try to use Xubuntu in live mode, there is no freezes in video(when laptop lid is close, and video play on secondary screen)...

---

### Post by fallout4all on 2013-05-07
The problem was in Desktop Environment...change to XFCE and bug is gone

---

