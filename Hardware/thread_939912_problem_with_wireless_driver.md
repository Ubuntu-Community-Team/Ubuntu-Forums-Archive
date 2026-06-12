---
title: "problem with wireless driver"
date: 2008-10-06
forum: Hardware
---

### Post by nikos.math on 2008-10-06
I have a dell latitude D520 and i cannot find the firmware.the driver is
(Broadcom B43 wireless driver) what i have to do to fix my wireless

---

### Post by sergiom99 on 2008-10-06
please post the output of this command typed in a console shell:
lspci

---

### Post by nikos.math on 2008-10-06
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by sergiom99 on 2008-10-06
I got mine working with this simple tutorial:
[http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)
Its for an HP, just go to the "Broadcom Wireless Card" section and follow the instructions. Should work like a charm.
(Credits to dark_stang for that)

---

### Post by nikos.math on 2008-10-06
sergiom 99 thanx for your help but I try this and nothing..

---

### Post by sergiom99 on 2008-10-06
did you get any error message??
It says you need to run a script and it will install everything for you.
The older version is a manual install. Follow this instructions and post back any errors for us to help you:
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750) (goto "Wireless Card Setup")

---

### Post by nikos.math on 2008-10-07
no error message..
i do it manual and everything is ok
anything else?

---

### Post by sergiom99 on 2008-10-07
well, reboot and try to connect to a wi-fi network.

---

### Post by nikos.math on 2008-10-07
i do it but nothing at all..

ubuntu see the card but not the wireless networks

lo no wireless extensions.

wlan0 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:32 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0 no wireless extensions.

---

### Post by nikos.math on 2008-10-07
eurithing is ok..
wireless connection ok 
i dont now how but is ok and i am happy
thanx sergiom99

---

