---
title: "Problem with mp3 player"
date: 2013-03-26
forum: Hardware
---

### Post by linuxonbute on 2013-03-26
I have a cheap Technica mp3 player which I have not used for some time, before I installed 12.04.
When I plug it in now I does not mount but it always used to.

I booted a live PCLinuxOS disc and it mounted and I could browse it with the file manager.
I rebooted Ubuntu and there it was - mounted and again I could browse it with file manager.
When I rebooted again it would no longer mount.
> 
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 13d1:7017 A-Max Technology Macao Commercial Offshore Co. Ltd. 
Bus 001 Device 003: ID 064e:f261 Suyin Corp. 
Bus 005 Device 002: ID 04d9:2519 Holtek Semiconductor, Inc. 

dmesg
 [  368.476223] usb 2-1: new high-speed USB device number 4 using ehci_hcd



gparted does not see it and neither does file manager.

It is Bus 002 Device 004: ID 13d1:7017 A-Max Technology Macao Commercial Offshore Co. Ltd. 
I have seen numerous cases where this happens with lots of different mp3 players which ubuntu does not seem to handle properly while other Linux distros do work. Is there something wrong with ubuntu? (for those who don't know PCLinuxOS is debian based also )
Is there anything I can do to fix this?

---

### Post by linuxonbute on 2013-03-27
Well I guess it's not just confined to Ubuntu. I selected 'eject' from file manager while running PCLinuxOS, removed the cable then plugged it back in and it wan't mounted. For some reason if I boot PCL and it see's the player then it mounts it but then no matter how many times I reboot PCL it then doesn't. The if I boot Ubuntu it see's it the first time then not on subsequent boots. Go back to PCL and round we go again.
What's happening here????
Even a complete shutdown doesn't seem to clear up the problem.

---

