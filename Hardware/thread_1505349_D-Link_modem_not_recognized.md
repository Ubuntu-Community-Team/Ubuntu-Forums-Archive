---
title: "D-Link modem not recognized"
date: 2010-06-09
forum: Hardware
---

### Post by The Recorder on 2010-06-09
Just got a new D-Link ADSL 2650U Modem/Router from my service provider.  Ubuntu Lucid doesn't see it - It has the 2.6.32-22 Kernel.  Mint 9 Live "and" installed, with the 2.6.32-21 Kernel, sees it fine, and has no problems with it.  Is this a Kernel issue?  Anyone with some thoughts or possible solutions?

Thanks

---

### Post by The Recorder on 2010-06-09
Before this gets lost in the vastness of this forum, thought that I'd push for at least someone's opinion.  I'd like to know if I should upgrade the Kernel in Mint (when it becomes available).

---

### Post by ronnielsen1 on 2010-06-09
What's the output of lsusb in terminal?

---

### Post by The Recorder on 2010-06-09
> **ronnielsen1 said:**
> What's the output of lsusb in terminal?

arthur@arthur-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:0809 Logitech, Inc. 
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
arthur@arthur-desktop:~$

Why would you want to know this?  The modem is not a USB modem - It's plugged directly into my ethernet port on my desktop computer.  By the way, Windows XP also sees the modem, and there are no problems with it.

---

### Post by fr3ak.m3 on 2010-06-09
remove the cable and then add again an then provide me the info of "dmesg | tail" (without quotes)

---

### Post by The Recorder on 2010-06-09
> **fr3ak.m3 said:**
> remove the cable and then add again an then provide me the info of "dmesg | tail" (without quotes)

arthur@arthur-desktop:~$ dmesg | tail
[   25.152008] eth0: no IPv6 routers present
[   31.988033] end_request: I/O error, dev fd0, sector 0
[   32.040030] end_request: I/O error, dev fd0, sector 0
[   34.245444] ISO 9660 Extensions: Microsoft Joliet Level 3
[   34.267077] ISOFS: changing to secondary root
[  115.560715] EXT4-fs (sdb7): recovery complete
[  115.561086] EXT4-fs (sdb7): mounted filesystem with ordered data mode
[  162.248453] e1000e: eth0 NIC Link is Down
[  172.754522] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  172.754527] 0000:02:00.0: eth0: 10/100 speed: disabling TSO
arthur@arthur-desktop:~$

---

### Post by The Recorder on 2010-06-09
Any further suggestions on this?

---

