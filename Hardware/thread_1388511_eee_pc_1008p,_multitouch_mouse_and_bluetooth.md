---
title: "eee pc 1008p, multitouch mouse and bluetooth"
date: 2010-01-23
forum: Hardware
---

### Post by brittney on 2010-01-23
Hi!
Anyone knows how to get the multitouch mouse and the bluetooth to work in 9.10? ive got everything else working out of the box.

cheers
-bri

---

### Post by aljoriz on 2010-01-23
I'm guessing that 1008p is very similar to 100pe

taken from [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

As with the 1005HA, most of the stuff works fine out  of the box, although there are some minor wireless connection issues. 
Issues: 

[LIST]
[*]The  microphone issue with the 1005HA seems to be present ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/449855](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/449855)).  
[*]Wireless works out of the  box, but connection is flaky. To fix, open a terminal and type 'sudo  apt-get install linux-backports-modules-wireless-karmic-generic' 
[*]Multi-touch has not been tested. It is likely that the  issue mentioned in the 1005HA will be present as it appears to be the  same hardware.
[/LIST]

---

