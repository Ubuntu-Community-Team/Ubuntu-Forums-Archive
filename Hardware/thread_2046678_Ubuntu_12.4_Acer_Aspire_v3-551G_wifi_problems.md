---
title: "Ubuntu 12.4 Acer Aspire v3-551G wifi problems"
date: 2012-08-23
forum: Hardware
---

### Post by linsms on 2012-08-23
Hi,

I've just buy a laptop and install an SSD and ubuntu on it. The boot time is amazing, but it's another history...

But... the wifi doesn't work propertly. It detects the network (wpa2) and it connects randomly, not usable, but... It disconect any other device connected to the AP.
Some logs:
```
Aug 23 18:51:27 knotatil2 kernel: [ 1899.709573] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Aug 23 18:51:30 knotatil2 wpa_supplicant[1062]: Trying to authenticate with 80:c6:ab:08:76:41 (SSID='MyWifi' freq=2412 MHz)
Aug 23 18:51:30 knotatil2 NetworkManager[950]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 23 18:51:30 knotatil2 kernel: [ 1902.194803] wlan0: authenticate with 80:c6:ab:08:76:41 (try 1)
Aug 23 18:51:30 knotatil2 kernel: [ 1902.392122] wlan0: authenticate with 80:c6:ab:08:76:41 (try 2)
Aug 23 18:51:30 knotatil2 kernel: [ 1902.592029] wlan0: authenticate with 80:c6:ab:08:76:41 (try 3)
Aug 23 18:51:30 knotatil2 kernel: [ 1902.792120] wlan0: authentication with 80:c6:ab:08:76:41 timed out
Aug 23 18:51:35 knotatil2 wpa_supplicant[1062]: Authentication with 80:c6:ab:08:76:41 timed out.
Aug 23 18:51:35 knotatil2 NetworkManager[950]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 23 18:51:35 knotatil2 NetworkManager[950]: <info> (wlan0): supplicant interface state: disconnected -> scanning

```
```
lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9903
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```

---

### Post by alexiicom on 2012-08-24
Hi !

I've the same configuration and the same problem :(

---

### Post by linsms on 2012-08-29
No one have solutions?

---

### Post by Adokas on 2012-09-06
I'm suffering from same issue too. It's really annoying, I hope someone know/find a solution.

---

### Post by linsms on 2012-09-06
I don't find a solution

---

### Post by alexiicom on 2012-09-07
Hi All!

I have a solution (not my, many url`s in INet):
"
**$sudo nano /etc/modprobe.d/ath9k.conf**
adding
**options ath9k nohwcrypt=1**
and rebooting.
"
9 hours - normal flight :D

---

### Post by linsms on 2012-09-07
It Works!!!
Thanks, now I can work with linux in my laptop.
:D:D:D

---

### Post by Adokas on 2012-09-08
Unfortunately it didn't work for me.

---

### Post by kocks on 2013-08-18
try looking here [http://pleph.appspot.com/init/posts/view/2657865](http://pleph.appspot.com/init/posts/view/2657865)
PS i know it is a diff card but it worked for my on my V3-571g

---

