---
title: "Bluetooth audio becomes choppy after a few minutes of inactivity"
date: 2023-02-10
forum: Hardware
---

### Post by alan.m.howard on 2023-02-10
Hi everyone,

After installing Ubuntu 22.04 on a 2013 iMac the audio quality on my Bluetooth headphones has become very unstable. It was working well previously on Ubuntu 18.04.

Immediately after connecting the headphones (Sennheiser HD 4.50) the quality is good, however after some time the sound becomes very choppy and poor quality. If I leave a single audio track playing this doesn't happen, but if I pause a video for a few minutes and come back it nearly always does. If I have the blueman applet open I can see the data transmission rate drops from ~45 KB/s to <10 KB/s when the problems start.

Disconnecting and reconnecting the headphones results in a good quality connection again, at least temporarily. 

Some additional notes from reading similar posts:
[LIST]
[*]The audio profile is not changing. I can still change to HFP (and can hear the difference), but changing back to A2DP does not restore the original audio quality.
[*]Restarting pulseaudio doesn't help 
[*]Wifi is disabled in the system settings.
[/LIST]

Output of lspci -knn | grep Net -A3; lsusbl

```
03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
	Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b:0111]
	Kernel driver in use: wl
	Kernel modules: bcma, wl
04:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)
	Subsystem: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686]
	Kernel driver in use: tg3
	Kernel modules: tg3
04:00.1 SD Host controller [0805]: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 01)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 05ac:828d Apple, Inc. Bluetooth USB Host Controller
Bus 001 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 004: ID 05ac:8511 Apple, Inc. FaceTime HD Camera (Built-in)
Bus 001 Device 003: ID 045e:07b2 Microsoft Corp. 2.4GHz Transceiver v8.0 used by mouse Wireless Desktop 900
Bus 001 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Any help would be greatly appreciated. I have the impression that some process related to either audio or Bluetooth is going into an idle state while not being used but is then not waking up again properly, but I'm not sure how to confirm this.

---

