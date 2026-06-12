---
title: "Mozilla really choppy after dist-upgrade"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by Bauldrick on 2007-03-15
I've been trying to get Ubuntu set up my laptop so that it's useable.
Using 6.10 seems the best - but after upgrading from previous version my browser becomes unbearably "choppy" scrolling vertically.

My laptop

Fujitsu Siemens - Amilo L7320GW

Graphics card seems to be some VIA 

When I do cat /etc/X11/xorg.conf I see it using defaults (vesa??) and generic

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"

But if I sudo dpkg-reconfigure -phigh xserver-xorg

and use via as opposed to vesa, upon reboot I get no screen and have to sudo dpkg-reconfigure -phigh xserver-xorg and switch back to vesa

Any help, this wasnt the case when installed it all smooth

---

### Post by taurus on 2007-03-15
You need to install a driver for your graphic card since vesa is a generic driver though.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by Bauldrick on 2007-03-15
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)


cheers

---

### Post by Bauldrick on 2007-03-15
For my future reference - follow this

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

