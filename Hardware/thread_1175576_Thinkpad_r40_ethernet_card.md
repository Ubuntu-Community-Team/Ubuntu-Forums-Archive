---
title: "Thinkpad r40 ethernet card"
date: 2009-06-01
forum: Hardware
---

### Post by somuchfortheafter on 2009-06-01
Greetings all.

I just purchased a thinkpad r40 that features an Intel Pro 100 VE network card. I loaded ubuntu 9.04 onto it last night, wireless seems to be fine however the ethernet card is not working at all. By that I mean that it cannot get an ip from dhcp, or when given a static IP use that.

lspic
```

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:02.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)

```

lsmod | grep e100
```

e100                   41356  0 
mii                    13440  1 e100

```

ifconfig eth0
```

eth0      Link encap:Ethernet  HWaddr 00:06:1b:da:aa:6e  
          inet6 addr: fe80::206:1bff:feda:aa6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8240 (8.2 KB)  TX bytes:16760 (16.7 KB)

```

Any suggestions?

---

### Post by somuchfortheafter on 2009-06-01
Upon more inspection, I left it online with crunchbang running, the ethernet card will connect and when I run "dhclient eth0" it connects just find and holds a connection.


However if I reboot the machine and leave it connected it will connect to the network every 4 minutes or so, but without manually running dhclient it never grabs an IP address.

I can tell it connects by looking at the switch to see when the port lights up... that is the only notification I receive.

---

### Post by somuchfortheafter on 2009-06-01
erm... solved.... not sure how but the issue seems to have resolved itself.

---

