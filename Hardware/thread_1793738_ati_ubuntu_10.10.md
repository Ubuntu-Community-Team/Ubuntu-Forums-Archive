---
title: "ati ubuntu 10.10"
date: 2011-06-29
forum: Hardware
---

### Post by snafu006 on 2011-06-29
Need ATi Xpress 200m drivers i have tryed all ati drivers and can get them to work can some one help me.

---

### Post by mastablasta on 2011-06-30
you need to use opensource drivers. more here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
also you can upgrade the opensouce drivers to latest version via PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by snafu006 on 2011-06-30
i have thos right now and i get very low frame rate.

---

### Post by mastablasta on 2011-06-30
are you running unity? EDIT: Ups or is that on Lubuntu?
 
what are full system specs?

---

### Post by snafu006 on 2011-06-30
See i have tryed 11.04 and fedora mesa drivers 7.11 the FGLRX drivers and all the drivers from here [http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx) i have look at old post and the only thing i can think of is to downgrade to 9.04 or 9.10
 
Ubuntu 10.10
Toshiba tecra A8-EZ8311
ATi Xpress 200M 128mb
120 GB HD
1.5 GB Ram

```
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
[COLOR=Red]01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M][/COLOR]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

```
 snafu@snafu-TECRA-A8:~$ dpkg -l '*fglrx*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  fglrx-modalias 2:8.780-0ubunt Identifiers supported by the ATI graphics dr
 
```

---

### Post by snafu006 on 2011-06-30
Bump

---

