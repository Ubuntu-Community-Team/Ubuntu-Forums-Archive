---
title: "32-bit Server 10.04 on IBM T43: No wireless, Fn+F5 not working"
date: 2010-08-04
forum: Hardware
---

### Post by breadoo on 2010-08-04
Hi,

I just installed the 32-bit **server** (no GUI), version 10.04 on an **IBM T43**. The wireless radio doesn't work - I tested this by trying to ping other machines on the network (via LAN cable connection, ok. Then via wireless, failed to ping). Also, Fn+F5 doesn't seem to be able to switch off the radio LED. Below is an excerpt from lshw, showing the Wireless interface:

```
  [COLOR="Red"]*-network DISABLED[/COLOR] (but strangely, wireless LED keeps blinking!)
       description: Wireless interface
       product: **PRO/Wireless 2200BG [Calexico2] Network Connection**
       vendor: Intel Corporation
       logical name: eth1
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: 
            pm 
            bus_master 
            cap_list 
            ethernet 
            physical 
            wireless
       configuration: 
            broadcast=yes 
            driver=ipw2200 
            driverversion=1.2.2kmprq 
            firmware=ABG:9.0.5.27 (Dec 12 2007) 
            latency=64 
            link=no 
            maxlatency=24 
            mingnt=3 
            multicast=yes 
            wireless=unassociated
       resources: irq:21 memory:a8401000-a8401fff

```

I am new to linux, and don't know how to go about fixing this via only the command line. Does anyone have experience with making the wireless radio and its associated Fn+F5 key work for the T43, **without** going through a GUI? Thanks!

---

### Post by Fafler on 2010-08-04
Which steps have you made to setup the wireless network? It's a bit more complicated than inserting the ethernet cable. You have to look at the commands iwconfig, ifconfig and dhclient. If you use WPA encryption you also need wpa_supplicant.

To connect to an unsecured network called test:

ifconfig eth1 up
iwconfig eth1 essid test
dhclient eth1

The [COLOR=Red]*-network DISABLED[/COLOR][FONT=monospace][/FONT] message is probably just because the networ isn't setup. Supply some info about your network setup if you need more help.

---

### Post by utilitytrack on 2010-08-04
to **breadoo**

Give here more diagnostics info:
```
$ grep IPW /boot/config-`uname -r`
$ lspci -nn
$ dmesg | grep -i ipw
# lsmod | grep ipw
# iwlist scan
# ifconfig
# cat /etc/network/interfaces
```

and I suppose that this device need some firmware installed:
```
$ dpkg -l *ipw*

```[FONT=Courier New]
[/FONT]

did you have NetworkManager installed? if yes, turn off it:
```
# /etc/init.d/NetworkManager stop

```[FONT=Courier New]
[/FONT]

---

### Post by breadoo on 2010-08-04
Thanks Fafler and utilitytrack for your replies. As per your suggestions, I have gathered more data on my network:


```
**ifconfig eth1 up**
SIOCSIFFLAGS: Permission denied

**iwconfig eth1 essid <MYSSID>**
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Operation not permitted.


**sudo dhclient eth1**
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/<SOME_MAC>
Sending on   LPF/eth1/<SOME_MAC>
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21


**dmesg | grep -i ipw**
[   36.713005] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   36.713009] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   36.713106] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   36.714023] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   36.714078] ipw2200 0000:04:02.0: firmware: requesting ipw2200-bss.fw
[   37.501901] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

**lsmod | grep ipw**
ipw2200               135152  0
libipw                 39896  1 ipw2200
lib80211                5046  2 ipw2200,libipw

**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: SOME_MAC
                    ESSID:"MY_SSID"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-46 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 524ms ago

                    
**cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
                    
**/etc/init.d/NetworkManager stop**
-bash: /etc/init.d/NetworkManager: No such file or directory

```

---

### Post by utilitytrack on 2010-08-04
to** breadoo**

please remember that all operations with network subsystem can make **root** only

---

