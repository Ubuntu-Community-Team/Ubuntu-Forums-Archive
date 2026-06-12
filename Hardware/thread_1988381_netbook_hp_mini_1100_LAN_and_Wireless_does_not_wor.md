---
title: "netbook hp mini 1100 LAN and Wireless does not work at all"
date: 2012-05-27
forum: Hardware
---

### Post by gabak on 2012-05-27
i got two netbook and i tried from ubuntu 9.10 to the last version 12.04 and neither of those funtion works at all.
same happend with any version of linux Mint.
why? why?
windows 7 does just fine , open the box ,no drivers needed all works from the end of the instalation til now.
FLAWLESS !!!

can linux mint make a paid version or something that if we have to pay for licencing or whatever to make it work like windows. it is 2012 and linux does nt work right like windows does.

i have being using linux since 2008 and fighting with it since the begining , in desktop computers always seem to works better than laptops in general. I m computer guy and i like it but sometime it make me mad.

any solution how to solve this issue?

ethernet card marvell yukon 88e8040 pci-e
wireless card broadcom 802.11g

it never happend to me in linux ethernet card wont work after instalation


thank you in advance.
and for letting me vent

gabe

---

### Post by bohemian9485 on 2012-05-27
Maybe [COLOR=Red]**[this article]("https://wiki.archlinux.org/index.php/Broadcom_wireless")**[/COLOR] can resolve your Broadcom wireless interface problem.

First we have to know your card's PCI-ID and correct model by using the command: ```
lspci -vnn | grep 14e4
```In my case:
```

rey@rey-netbook:~$ lspci -vnn | grep 14e4
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]

```I'm using Broadcom BCM4313 802.11 b/g/n wireless controller with PCI-ID 14e4:4727.

After you got the correct model and PCI-ID of your wireless interface, consult the above article so you will know the correct driver to use.

---

### Post by gabak on 2012-05-27
thxs for your help
main issue is the ethernet card that does nt work.
how can i fix the wireless one if i cant get data into my pc?

hp@hp-HP-Mini:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
hp@hp-HP-Mini:~$ lspci -vnn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by bohemian9485 on 2012-05-28
I think Marvell has a Linux driver for the Marvell Yukon 88e8040 PCI-E Fast Ethernet Controller. Go to their _**[support page]("http://www.marvell.com/support/downloads/search.do")**_.

---

### Post by gabak on 2012-05-28
yes sure there is a driver but ...
how do you download it and install it if the netbook has no internet at all.
i know how to do those thing in win but linux no clue

> **bohemian9485 said:**
> I think Marvell has a Linux driver for the Marvell Yukon 88e8040 PCI-E Fast Ethernet Controller. Go to their _**[support page]("http://www.marvell.com/support/downloads/search.do")**_.

---

### Post by wildmanne39 on 2012-05-28
Hi, Download the b43 zip file to a flash drive using a computer with internet, then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by bohemian9485 on 2012-05-28
Just like wildmanne39 said, download the driver to usb drive from a computer with Internet connection and copy the file to your netbook desktop.

---

