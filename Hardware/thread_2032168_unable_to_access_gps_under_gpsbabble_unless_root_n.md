---
title: "unable to access gps under gpsbabble unless root not Garmin"
date: 2012-07-23
forum: Hardware
---

### Post by thod on 2012-07-23
I am running Ubuntu 12.04LTS and have problem connecting using gpsbabel to my Qstars Q1000Ex device unless I use sudo.

running
gpsbabel -w -t -i mtk,erase -f /dev/ttyACM0 -o gpx -F test3.gpx
gives
Failed to open port (Permission denied)
mtk_logger: Can't initialise port "/dev/ttyACM0" (Permission denied)

running
sudo gpsbabel -w -t -i mtk,erase -f /dev/ttyACM0 -o gpx -F test3.gpx
gives no errors. and the file test3.gpx is ok.

I found this forum thread
[http://ubuntuforums.org/showthread.php?t=1945665](http://ubuntuforums.org/showthread.php?t=1945665)

So I
ran lsusb without logger
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 1a40:0201 Terminus Technology Inc. Hub
Bus 001 Device 004: ID 0557:8021 ATEN International Co., Ltd 
Bus 001 Device 005: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 007: ID 1038:0210 Ideazon, Inc. 

and lsusb with logger
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 1a40:0201 Terminus Technology Inc. Hub
Bus 001 Device 004: ID 0557:8021 ATEN International Co., Ltd 
Bus 001 Device 005: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 010: ID 0e8d:3329 MediaTek Inc. 
Bus 001 Device 007: ID 1038:0210 Ideazon, Inc. 

And figured 
Bus 001 Device 010: ID 0e8d:3329 MediaTek Inc.  must be the logger?

so I added a q1000.rules to /etc/udev/rules.d/ using
sudo gedit /etc/udev/rules.d/q1000.rules

and added lines
#Qstarz Q1000Ex
SUBSYSTEM=="usb", ATTR{idVendor}=="0e8d", ATTR{idProduct}=="3329", MODE="0666"

as seemed to work with the beforementioned thread.
Rebooted my system
No luck :(

after looking around I found someone mentioning dmesg so I ran it and found these lines
[ 2173.393175] usb 1-1.2.5: new full-speed USB device number 10 using ehci_hcd
[ 2173.488828] cdc_acm 1-1.2.5:1.1: ttyACM0: USB ACM device

I dont know if they are needed for something but I post them anyway.

And I'm sorry if I post this in the wrong place or if it's already answered somewhere, but in that case I did not find it.

---

