---
title: "unity on radeon 9200 (possible gl issue)"
date: 2011-07-20
forum: Hardware
---

### Post by baskak on 2011-07-20
hi, i have an ati radeon 9200, and no unity on 11.04. "unity_support_test -p" gives the following: [http://paste.ubuntu.com/647158/](http://paste.ubuntu.com/647158/), however the card IS capable of gl 1.4 ([http://en.wikipedia.org/wiki/Radeon](http://en.wikipedia.org/wiki/Radeon)). it's running on default driver, there are no additional drivers available, and to my knowledge currently only the  included drivers support radeon 9200 ([http://ubuntuforums.org/showthread.php?t=1540387](http://ubuntuforums.org/showthread.php?t=1540387)).
unfortunately ubuntu irc channel didn't offer me help. thx in advance.

---

### Post by ajgreeny on 2011-07-20
I think that card is simply not man enough to run unity.

I have the same card in my old desktop with 2GB ram and sempron 2400+ cpu, but it defaults to classic desktop, though will run unity 2d.

I don't like unity from what I have seen of it on my netbook, so it does not worry me at all, and if unity becomes the only desktop available for ubuntu in future, I shall probably just move to one of the other versions of the ubuntu family, xubuntu or kubuntu or lubuntu.  I started using Linux and ubuntu about 6 years ago with KDE then hated it when v4 first came along.

I am now looking at all the alternatives to gnome 3 and unity so that I know where to jump if I decide that unity, even when it is beyond the current "work in progress" stage, is not my choice.

---

### Post by nego0 on 2011-08-11
Can  i run unity with ati radeon 9200 SE

lspci:
```
shinobixlockon@shinobixlockon-HP-d530-CMT-DG745A:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
[COLOR="Blue"]01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)[/COLOR]
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:09.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
shinobixlockon@shinobixlockon-HP-d530-CMT-DG745A:~$ 

```

---

