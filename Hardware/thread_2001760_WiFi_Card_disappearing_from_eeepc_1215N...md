---
title: "WiFi Card disappearing from eeepc 1215N.."
date: 2012-06-11
forum: Hardware
---

### Post by Krakken on 2012-06-11
Hi everyone,
I experienced this proble a couple of times before upgrading to Ubuntu 12.04 and now, 5 days after succesfull upgrade is back and I cannot solve it.

I own a eeepc 1215N with Ubuntu 12.04 now, and while surfing the web once in a while the wireless signal disappears. At that point the wireless option in the connectivity menu is not longer listed, and also after booting there is no sign of wifi connectivity. The sad part is that under windows it works perfectly.

Here are the output of my lspci:

```
pbd@pbd-1215N:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
04:00.0 VGA compatible controller: NVIDIA Corporation Device 0a76 (rev a2)

```

Seems to me that my wifi card is not even listed here as it is when is properly working...

Can someone help me??

Many respectfull thanks!!

---

### Post by Krakken on 2012-06-14
...and now is back up again, disappearing once in a while...hectic behaviour..after few hours off the wireless restart and then disapper after few minute use...

here is the lspci when the wireless is working:

```

pbd@pbd-1215N:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 VGA compatible controller: NVIDIA Corporation Device 0a76 (rev a2)

```

What should I do???

---

### Post by SeaKing on 2012-06-14
Well I've experienced lots of trouble with broadcom wireless adapters what might help is to re-/install the driver: [http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working](http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working)

---

### Post by Krakken on 2012-07-06
It works again!! Many Thanks.
K

---

