---
title: "Intel 2200BG - xsupplicant &amp; LEAP"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by Hoshimaru on 2005-03-08
Hello everyone :)

As you can see I'm new here. I'm using Ubuntu now since approximately a month. Before I was using Gentoo, but I damaged it badly by installing mono 1.1.4 from svn.

Anyway, mono is working with ubuntu as well as all the other development tools I need.

Today, I was looking on how to connect to a wireless network with LEAP authentication while waiting for my brother at his school. To do so, I installed xsupplicant.

First, I did a *# iwlist eth1 scanning*
```
root@hoshimaru:~ # iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:0C:F6:03:33:70
                    ESSID:"Sitecom"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rate:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Extra: RSSI: -65  dBm
                    Extra: Last beacon: 3ms ago
          Cell 02 - Address: 00:40:96:40:7D:FA
                    ESSID:"PHL-STUD"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:11 Mb/s
                    Extra: Rates (Mb/s): 5.5 11
                    Extra: RSSI: -61  dBm
                    Extra: Last beacon: 12ms ago
          Cell 03 - Address: 00:40:96:55:3E:1D
                    ESSID:"PHL-STUD"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Extra: RSSI: -65  dBm
                    Extra: Last beacon: 0ms ago
```

To connect to the network, I modified my shell script I use for my home lan.
Let's say I want to connect to cell 02
```
#!/bin/bash
iwconfig eth1 essid "PHL-STUD"
iwconfig eth1 mode managed
iwconfig eth1 key open
iwconfig eth1 channel 6
ifconfig eth1 up
xsupplicant -c /root/wlan.phl.xsupp
sleep 20
dhclient eth1
```

And wlan.phl.xsupp is looking like this:
```
network_list = phl
default_netname = phl
first_auth_command = <BEGIN_COMMAND>echo "Connected"<END_COMMAND>
logfile = /var/log/xsupplicant.log
deny_interfaces = lo, eth0

phl {
    type = wireless
    ssid = <BEGIN_SSID>PHL-STUD<END_SSID>
    identity = <BEGIN_ID>2**0*9*<END_ID>
    allow_types = eap_leap

    eap_leap {
        username = <BEGIN_UNAME>2**0*9*<END_UNAME>
        password = <BEGIN_PASS>*pass*<END_PASS>
    }
}
```
(username & pass altered with * )

Running my leap.sh script doesn't show anything particular, except it's not getting an IP is DHCP seems to broadcast all around.

When I try with my brother's Cisco Aironet 350 using the Cisco tools, I get this:
```
User: 2****** authenticated
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
wifi0: unknown hardware address type 801
sit0: unknown hardware address type 776
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:07:0e:b9:0c:62
Sending on   LPF/eth1/00:07:0e:b9:0c:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
```

I get more or less the same output with my intel & xsupplicant.
Running xsupplicant alone says I'm authed, but then, I can't get an IP.

Who knows how I can get LEAP running ? I'd try it myself at home should I've a Cisco AP. My Linksys WRT54G doesn't support LEAP (Linksys firmware)

The one who knows how to solve this will make 2 new Ubuntu very happy

---

### Post by Hoshimaru on 2005-03-09
No one ever tried Leap ?

---

### Post by germinator on 2005-03-10
[QUOTE=Hoshimaru]No one ever tried Leap ?[/QUOTE]
 Well i don't have any solution but I'm looking for it...if you find it, tell me ;-0

---

### Post by Derek Djons on 2005-04-05
I have tried to configure Xsupplicant in combination with SuSE and PAP-TTLS protocol which is being used at my school.

Since SuSE has Xsupplicant in it's package manager I can't tell anything about the installation procedures. After the package manager downloaded and installed Xsupplicant I used the official manual which can be found at [www.open1x.org](www.open1x.org)

I configured the main config file of Xsupplicant. Then I wrote myself another config file which Xsupplicant used to authenticate. When I was running the script by executing:

xsupplicant <place where the config file is located>/<config filename> -f it showed me some detailed information which I never saw before. The only thing which I have to arrange is getting the .pem (permission) files since Xsupplicant or SuSE will download them automatically (for as far as I know).

But since Xsupplicant isn't recognizing your hardware properly I guess something went wrong during installation. Could you tell us which kind of (wirless) network cards you are using? Intel 2100 or 2200 I assume?

---

### Post by Hoshimaru on 2005-04-06
Hi,

It's a Intel 2200BG built-in wireless adaptor.

---

### Post by Derek Djons on 2005-04-06
[QUOTE=Hoshimaru]Hi,

It's a Intel 2200BG built-in wireless adaptor.[/QUOTE]

Interesting. For as far as I know Xsupplicant doesn't mess with the ipw-firmware (Intel 2200BG drivers).

When you use the network card without Xsupplicant and without LEAP does the card receive an IP?

---

### Post by Hoshimaru on 2005-04-06
Sure, it works perfectly without LEAP and Xsupplicant on my home wireless lan.
No complaining on that side.

---

