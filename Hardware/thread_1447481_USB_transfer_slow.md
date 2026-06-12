---
title: "USB transfer slow"
date: 2010-04-05
forum: Hardware
---

### Post by challenger10 on 2010-04-05
I have a dell Inspiron 1420, running on Karmic. My usb to hdd  transfer rate is under 700 kbps but I recently noticed that if I have my XP running on Virtual Box, the transfer rate gets better, around 12-13 mbps, my inbuilt memory card slot which Ubuntu was not detecting gets read and has a decent transfer rate as well and I have a Nikon d-40 which also is only detected when the Virtual Box is running.
I'm new to Ubuntu, I went through some forums and I changed the fstab as well as one person suggested but nothings been working till now, 

here's my lsusb

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 008: ID 046d:c526 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

thanks for the help.

challenger

---

### Post by mörgæs on 2010-04-06
This bug has been around for a while:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762?comments=all)

There are some advice in the bug report, but I can not guarantee that you will get up to Windows speed (this time I shall not spell it Windoze).

An easy test is live booting version 10.04 beta for comparison, but I doubt that there will be much of a difference.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by cchhrriiss121212 on 2010-04-06
I had this problem and fixed it by formatting the usb drive from ntfs to ext4. This changed speeds from a patchy 2MB/s to 18MB/s. Not much use if you need to connect to windows machines though.

---

