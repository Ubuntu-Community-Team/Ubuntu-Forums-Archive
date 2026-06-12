---
title: "PW5110 UPS not operating via NUT"
date: 2009-11-05
forum: Hardware
---

### Post by Yancho on 2009-11-05
Hi,

I bought a PowerEdge 5110 some year ago and has used it for a Windows pc since. Lately I have changed my whole network to a Linux network porting all machines to Ubuntu. The current workstation to where the P/Edge is connected is Ubuntu 9.04 64bit ( Linux yancho-ubuntu 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64 GNU/Linux )

I have followed tutorials to set up NUT to be able to provide me with UPS monitoring to no avail.

This is the info "dmesg" gives me:

[517097.193836] usb 5-2: new low speed USB device using uhci_hcd and address 10
[517097.404059] usb 5-2: configuration #1 chosen from 1 choice

This is the info "lsusb" gives me:

Bus 005 Device 010: ID 0592:0002 Powerware Corp. UPS (X-Slot)

I have set up NUT to the best of my knowledge and following: [http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/) 

nut.conf
--------
MODE=standalone

ups.conf
--------
[myups]
        driver = bcmxcp_usb
        port = auto
        shutdown_delay = 60
        desc = "PowerWare_5110_EatON"

upsd.conf
---------
ACL all 0.0.0.0/0
ACL localhost 127.0.0.1/32
ACCEPT localhost
REJECT all

upsd.users
----------
[root]
    password = testpass
    allowfrom = localhost
    instcmds = ALL
    actions = SET

[upsmon]
    password = testpass
    upsmon master


upsmon.conf
-----------
MONITOR myups@localhost 1 upsmon testpass master
POWERDOWNFLAG /etc/killpower
SHUTDOWNCMD "/sbin/shutdown -h now"


However when I try to test for UPS activity I get:

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


This is really starting to trouble me so I installed Poweware software naming the Network Shutdown Module and also the Personal Solutions Pac. For the latter I downloaded the 32bit module and using "getlibs" I installed it for my system.

The Network Shutdown Module is saying: "No device discovered." whilst the Personal Solutions Pac prompts a popup saying: "No UPS found. Check that your UPS USB or serial cable is plugged". 

I tried also following a compiling tutorial after I removed all the packages. The tutorial is: [http://www.networkupstools.org/doc/2.2.0/INSTALL.html](http://www.networkupstools.org/doc/2.2.0/INSTALL.html)

This has basically put me into a situation where I am without a UPS and basically have forked loads of money (here in Malta it is not cheap!) for absolutely nothing and having a server risking to be borked because of electricity.

Any help in solving this issue is extremely appreciated. 

Thanks and regards

Matthew

---

