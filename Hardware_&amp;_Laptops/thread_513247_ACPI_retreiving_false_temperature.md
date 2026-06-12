---
title: "ACPI retreiving false temperature"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by paddy2706 on 2007-07-30
Hello everyone, I'm really confused about my notebooks behaviour.
Today I upgraded all avaliable packages, which included:
> libisc
libdns22
libisccc0
libisccfg1
libbind9-0
libwres9
bind9-host
dnsutils
iptables
app-install-data-commercial
clamav-base
firefox-dom-inspector
firefox-gnome-support
libnss-dev
libnss3
libnspr-dev
libnspr4
firefox
qgview
lftp
php5-cli
php5-mysql
libapache2-mod-php5
php5-common
libcurl3
libcurl3-gnutls
libqt4-core
libqt4-gui
libqt4-sql
libqt4-qt3support
php5
wineand since, it always shuts down a few minutes after booting.
```
acpi -t
``` returns a temperature between 50 and 60 degrees celsius but sometimes (found this out using watch) it will return 128.0 for less than a second.
This seems to be a bad bug to me.
Disabling acpi before booting disables this strange behaviour.

anyone else experiencing this ?

regards,
paddy

ps: have my hardware configuration:
```
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:0e.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0e.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0e.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

---

