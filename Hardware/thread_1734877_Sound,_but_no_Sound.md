---
title: "Sound, but no Sound"
date: 2011-04-20
forum: Hardware
---

### Post by LinXNut on 2011-04-20
I have recently installed xubuntu onto a pretty old laptop. A Dell Latitude D520. So far it has been OK, I had some issues with the network earlier, but now its solved. The issue I have no is the sound. I play a game called vendetta online, and the sound works great in that. When i try to set volume or other things, there is no sound.

Here is my lspci:

```
jonathan@Xubuntu-Lap:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
jonathan@Xubuntu-Lap:~/Desktop$ 

```I am not too worried to be without sound. But it would be fun to tinker with it. :D

---

### Post by lidex on 2011-04-21
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by LinXNut on 2011-04-21
Sorry to get back so late, here is the link to the details for my sound...

[http://www.alsa-project.org/db/?f=cc01d0354da6319c93f27ff29ef7930eadb5b8fa](http://www.alsa-project.org/db/?f=cc01d0354da6319c93f27ff29ef7930eadb5b8fa)

It does not show my processor, but on my laptop, it says "Celeron M"

---

### Post by lidex on 2011-04-21
I see you're using pulseaudio - thought that wasn't in xubuntu install. Try removing your pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.pulse-cookie 

```
**Reboot**

Now these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

