---
title: "UPS Powerware 5110 NUT installation"
date: 2009-11-06
forum: Hardware
---

### Post by Yancho on 2009-11-06
Hi,

I bought a **PowerEdge 5110** some year ago and has used it for a Windows pc since. Lately I have changed my whole network to a Linux network porting all machines to Ubuntu. The current workstation to where the P/Edge is connected is Ubuntu 9.04 64bit ( Linux yancho-ubuntu 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64 GNU/Linux )

I have followed tutorials to set up NUT to be able to provide me with UPS monitoring to no avail.

This is the info "*dmesg*" gives me:

```
[517097.193836] usb 5-2: new low speed USB device using uhci_hcd and address 10
[517097.404059] usb 5-2: configuration #1 chosen from 1 choice
```This is the info "*lsusb*" gives me:

```
Bus 005 Device 010: ID 0592:0002 Powerware Corp. UPS (X-Slot)
```I have set up NUT to the best of my knowledge and following: [http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/) 

```
[B]nut.conf
--------[/B]
MODE=standalone
``````
[B]ups.conf
--------[/B]
[myups]
        driver = bcmxcp_usb
        port = auto
        shutdown_delay = 60
        desc = "PowerWare_5110_EatON"

``````
[B]upsd.conf
---------[/B]
ACL all [0.0.0.0/0]("http://0.0.0.0/0")
ACL localhost [127.0.0.1/32]("http://127.0.0.1/32")
ACCEPT localhost
REJECT all
``````
[B]upsd.users
----------[/B]
[root]
    password = testpass
    allowfrom = localhost
    instcmds = ALL
    actions = SET

[upsmon]
    password = testpass
    upsmon master
```
```
[B]upsmon.conf
-----------[/B]
MONITOR myups@localhost 1 upsmon testpass master
POWERDOWNFLAG /etc/killpower
SHUTDOWNCMD "/sbin/shutdown -h now"
```
However when I try to test for UPS activity I get:

```
yancho@yancho-ubuntu:/etc/nut$ sudo upsdrvctl -u root start myups 
Network UPS Tools - UPS driver controller 2.4.1
Network UPS Tools - BCMXCP UPS driver 0.21 (2.4.1)
USB communication subdriver 0.17
Can't set POWERWARE USB configuration
Unable to find POWERWARE UPS device on USB bus 

Things to try:

 - Connect UPS device to USB bus

 - Run this driver as another user (upsdrvctl -u or 'user=...' in ups.conf).
   See upsdrvctl(8) and ups.conf(5).

Fatal error: unusable configuration
Driver failed to start (exit status=1)
```
This is really starting to trouble me so I installed Poweware software naming the Network Shutdown Module and also the Personal Solutions Pac. For the latter I downloaded the 32bit module and using "getlibs" I installed it for my system.

The Network Shutdown Module is saying: "No device discovered." whilst the Personal Solutions Pac prompts a popup saying: "No UPS found. Check that your UPS USB or serial cable is plugged". 

This has basically put me into a situation where I am without a UPS and basically have forked loads of money (here in Malta it is not cheap!) for absolutely nothing and having a server risking to be borked because of electricity.

I have also tried to contact the suppleir and they informed me to remove both the Network Shutdown Module and Personal Solutions Pac. I did so and following their advice I removed also NUT and nother related software. I tried, following their advice to use the website  [http://www.networkupstools.org/doc/2.2.0/INSTALL.html](http://www.networkupstools.org/doc/2.2.0/INSTALL.html) as my tutorial. I compiled nut again and compiling and *make install* worked fine however when trying to start up the **upsdrvctl** I am still getting:

```
**root@yancho-ubuntu:/usr/local/****ups/etc# /usr/local/ups/bin/upsdrvctl -u root start**
Network UPS Tools - UPS driver controller 2.4.1
Network UPS Tools - BCMXCP UPS driver 0.21 (2.4.1)
USB communication subdriver 0.17
Can't set POWERWARE USB configuration
Unable to find POWERWARE UPS device on USB bus 

Things to try:

 - Connect UPS device to USB bus

 - Run this driver as another user (upsdrvctl -u or 'user=...' in ups.conf).
   See upsdrvctl(8) and ups.conf(5).

Fatal error: unusable configuration
Driver failed to start (exit status=1)
**root@yancho-ubuntu:/usr/local/****ups/etc# tail ups.conf**
[myupsname]
        driver = bcmxcp_usb
        port = auto
        desc = "Workstation"

[588267.256079] hub 5-0:1.0: unable to enumerate USB device on port 2
[588267.800034] usb 5-2: new low speed USB device using uhci_hcd and address 12
[588267.994723] usb 5-2: configuration #1 chosen from 1 choice
root@yancho-ubuntu:/usr/local/ups/etc# 

**root@yancho-ubuntu:/usr/local/****ups/etc# lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 012: ID 0592:0002 Powerware Corp. UPS (X-Slot)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0566:3002 Monterey International Corp. 
Bus 004 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 011: ID 093a:2620 Pixart Imaging, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Any help in solving this issue is extremely appreciated. 

Thanks and regards

---

### Post by gidra on 2009-12-04
I have same UPS but cannot find windows drivers, would appreciate if you tell me where I can download them from. Thanks

---

### Post by Menthu_Rae on 2010-04-03
Hey guys, you might want to try out my guide here - works perfectly in Lucid. Not sure about Karmic yet- I might give that a go tomorrow :)

[http://ubuntuforums.org/showthread.php?t=1443562](http://ubuntuforums.org/showthread.php?t=1443562)

**gidra**: For Windows drivers, simply go to the Eaton site:

[http://powerquality.eaton.com/Support/Software-Drivers/default.asp](http://powerquality.eaton.com/Support/Software-Drivers/default.asp)

Log in and you can then download LanSafe.

---

