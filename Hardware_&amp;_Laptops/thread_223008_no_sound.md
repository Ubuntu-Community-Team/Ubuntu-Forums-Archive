---
title: "no sound"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by zpro on 2006-07-25
have the lastest updates, but still no sound...
this is getting very old...

please anyone.....
here is lspci output:
lspci
0000:00:00.0 Host bridge: ATI Technologies Inc ATI Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10)
0000:03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
-----------
TKS :(

---

### Post by LordRaiden on 2006-07-25
Follow the guide in my signature. Your soundcard driver is atiixp (got it from [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ATI#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ATI#matrix))

Post back here if you get stuck.

---

### Post by HoneyGutClusters on 2006-09-25
Ok. I've been fighting sound on this same chip for a while now, and here's what I go so far...

Apparently, this is a bug with AC97. The best way to check is to attached external amplified speakers to the headphone out, play some sound, and crank the volume to max. If you're being affected by the bug, you'll hear sound, but it'll be very faint.

First, let's try the simple. Go into console and run "alsamixer". hit the right arrow and select "IEC958", then nit the "m" key to mute it. Hit escape twice to exit the program, then play some sound. This is what got audio working for me.

This is also listed on ALSA's bugtracker, along with a workaround.

workaround code:
```

cat > /proc/asound/IXP/codec97#0/ac97#0-0+regs <<EOF
00 0000
02 0a0a
04 0000
06 8000
08 0000
0a 0000
0c 8008
0e 8008
10 8808
12 8808
14 0000
16 8808
18 8808
1a 0000
1c 8000
1e 0000
20 0400
22 0000
24 0000
26 000f
28 09c4
2a 05f0
2c bb80
2e bb80
30 bb80
32 bb80
34 0000
36 8080
38 8080
3a 2000
3c 0000
3e 0000
40 0000
42 0000
44 0000
46 0000
48 0000
4a 0000
4c 0000
4e 0000
50 0000
52 0000
54 0000
56 0000
58 0000
5a 0000
5c 0000
5e 0000
60 0000
62 0000
64 0808
66 0808
68 0aea
6a 0040
6c 0000
6e 0025
70 81e0
72 22e8
74 8000
76 0000
78 0007
7a 2090
7c 414c
7e 4760
EOF

```
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1274]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1274")

When you try to run this command as sudo, it denies permission. you have to switch to root bu running "sudo -s -H" first, but then it outputs "no such device", despite the fact the device does exist.

---

