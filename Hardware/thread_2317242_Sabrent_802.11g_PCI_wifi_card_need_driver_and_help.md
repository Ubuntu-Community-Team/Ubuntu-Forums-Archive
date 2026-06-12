---
title: "Sabrent 802.11g PCI wifi card need driver and help"
date: 2016-03-14
forum: Hardware
---

### Post by WacoJohn on 2016-03-14
I need help in obtaining the driver and installing it to Lubuntu -32.  Fresh install of Lubuntu/updated.  Currenly connected ETHERNET.  The card came new out of the box, but it has been laying on a shelf for YEARS.  The box contains a mini CD with Linux drivers, but I have no clue how to implement.  Here is what is on the disk:



Folder PCI-802N(WNP671N)/LINUX
2008_0702_RT2860_Linux_SoftAP_v1.9.0.0.tar.bz2
2008_0708_RT2860_Linux_STA_v1.7.0.0.tar.bz2
2008_0708_RT2860_Linux_WebUI_v1.7.0.0.tar.bz2
ReleaseNote-R2860.txt

Folder PCI-G802(630G)/LINUX
2007_1210_RT61_Linux_STA_v.1.1.2.0.tar.bz2
2008_0506_RT61_Linux_SoftAP_Drv1.1.3.0.tar.bz2

All other folders refer to USB or MANUAL, or whatever.  These appear to be the only two concerning PCI.

Here is my current setup:

owner@Lubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GDH (ICH7R/ICH7DH) SATA Controller [RAID mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
01:03.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
01:04.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation NM10/ICH7 Family LAN Controller (rev 01)
owner@Lubuntu:~$

Any simple/clear help is GREATLY appreciated.  Thank you in advance.

---

### Post by WacoJohn on 2016-03-14
Looks like the driver is detected, now that I look closer at LSPCI.  I guess I need to know my 'SSID', BSSID, MAC address, and cloned MAC address.  DUH .... I rarely use WIFI ... Ethernet guy.  I REALLY feel dumb.  Still ... help appreciated.

---

### Post by weatherman2 on 2016-03-14
You might ask to have this thread moved to the Networking & Wireless forum.

An entry in "lspci" doesn't mean a driver was installed.  Run the command

```

sudo lshw -C network

```

to see what network connections were set up.

Even if there are drivers on that old disk, I wouldn't bother with them.

If the wireless card is working, it should detect any available wireless networks nearby and show you a list - and you choose one.  You shouldn't have to type in the SSID unless it is "hidden" intentionally (unusual).

---

### Post by WacoJohn on 2016-03-14
> **weatherman2 said:**
> You might ask to have this thread moved to the Networking & Wireless forum.

An entry in "lspci" doesn't mean a driver was installed.  Run the command

```

sudo lshw -C network

```

to see what network connections were set up.

Even if there are drivers on that old disk, I wouldn't bother with them.

If the wireless card is working, it should detect any available wireless networks nearby and show you a list - and you choose one.  You shouldn't have to type in the SSID unless it is "hidden" intentionally (unusual).

You are a true Prince.  THANK YOU.  Yes, .. LUBUNTU saw the PCI card all the while.  I just THOUGHT it didn't and I needed a driver.  I did not.  I did some dinking around with SSID and BSSID and pretty much got nowhere.  I think I rebooted the machine and to my pleasant surprise, got a list of available WIFI networks.  Picked one of mine and it is working fine.  That's when I came back and marked thread solved.

You are most kind, and I thank you for your wisdom and valuable time.

---

