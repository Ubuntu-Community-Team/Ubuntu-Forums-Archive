---
title: "Wireless and other problems"
date: 2008-07-16
forum: General Help
---

### Post by jamiesalter on 2008-07-16
hey guys...just got linux so still a complete noob (please speak slowly :) )

Installed Ubuntu on an Acer travelmate 250.  everything fine except the wireless doesn't work.  This is the result of an *lshw*
```
 *-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:8d:46:3f
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth0
                version: 10
                serial: 00:0a:e4:45:83:16
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

It seems that the problem lies with the "*wireless=radio off*".  Therefore have downloaded acerhk.  Here is a result of *cat /proc/driver/acerhk/info*:
```
Acer hotkeys version 0.5.34
Model(Type)	: (new)
request handler	: 0xc00fdc40
CMOS index	: 0x60
events pending	: 0
kernel polling	: active
autoswitch wlan	: disabled
```

I then tried ```
echo "1" > /proc/driver/acerhk/wirelessled
``` which gave me no joy.  However I did try *echo "1" > /proc/driver/acerhk/blueled* which successfully turned on bluetooth.

*cat /sys/class/net/*/device/rf_kill* returned "2".

Whilst pressing wireless button and trying all the above commands was viewing *tail -f /var/log/messages* to check for any response.  With the bluetooth got something, but not with the wireless.  The other problems I described in the title were that *tail -f /var/log/messages* produced messages of the following constantly:

```
Jul 16 20:17:56 ubuntu-laptop kernel: [ 1029.388634] sr: Sense Key : Hardware Error [current] 
Jul 16 20:17:56 ubuntu-laptop kernel: [ 1029.388639] sr: Add. Sense: Head select fault
Jul 16 20:17:58 ubuntu-laptop kernel: [ 1031.388030] sr: Sense Key : Hardware Error [current] 
Jul 16 20:17:58 ubuntu-laptop kernel: [ 1031.388035] sr: Add. Sense: Head select fault
```

Haven't researched the above (have spent too much time on the wireless) but could they be linked?

As a bit of background, I just installed the wireless card from another broken acer laptop.  Haven't tested it with windows yet, so it may just be not working as have installed it wrong.  However as the driver etc seems to appear in *lshw*, inclined to think the software is to blame.  Will show results of *dmidecode* if it may be useful.

Any helped is very much appreciated.

Cheers.

---

### Post by yram on 2008-10-18
There have been no replies yet to this question (that I can see), I would like to add that I too have this problem, though with a small twist:
The file that needs to be modified after upgrading to the new driver is:
/sys/bus/pci/driver/ipw3945/0000:05:00:0/rf_kill

This file holds a single value of 2 which needs to be changed to 0, signifying disable rf_kill.

As root, I cannot edit the file and keep the new file. After doing so with either vim or nano, re-writing and saving the changes, it is changed back to the value 2 again. I have changed permissions to rw rw rw, to no avail.
Any help here?
matthew

---

