---
title: "No /dev/ttyUSB* for device"
date: 2008-10-06
forum: Hardware
---

### Post by fuzzyfurfeet on 2008-10-06
I'm trying to connect to an HTC Smartphone via USB. I'm not interested in syncing yet; I just need to be able to get into the device through USB so I can flash the ROM using a tool called HTCFlasher. Ubuntu is running on a Dell Inspiron B130.

My first step is to get the USB device to show in the /dev/ttyUSB* directory, but it's not happening.

Some details:

me@ubu2bu:~$ tail -f /var/log/messages
Oct  7 09:44:15 ubu2bu kernel: [  112.410221] usb 1-1: new full speed USB device using uhci_hcd and address 3
Oct  7 09:44:15 ubu2bu kernel: [  112.419231] usb 1-1: configuration #1 chosen from 1 choice
Oct  7 09:44:15 ubu2bu kernel: [  112.510747] eth1: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, 80:00:60:0f:e8:00

me@ubu2bu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0bb4:0b52 High Tech Computer Corp. 
Bus 001 Device 001: ID 0000:0000  

Can anybody give me clues to get the device USB-visible?
:confused:
Thanks in advance!

---

### Post by phidia on 2008-10-06
The thread/howto [here]("http://ubuntuforums.org/showthread.php?t=901284") is for gutsy but it still should be usable.

---

### Post by fuzzyfurfeet on 2008-10-07
Thanks, phidia! That howto did it. The HTC device is now accessible through /dev/ttyUSB0.

However, it appears I have a problem with the flashing utility itself. HTCFlasher says it doesn't recognize the device when it tries to connect. Anybody have any experience with HTCFlasher? Is there another RUU (ROM Upgrade Utility) for HTC devices?

Thanks again,
:biggrin:

---

