---
title: "How to install gspca driver for ubuntu 8.10"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by Brij Bhushan on 2009-08-21
Hi I'm using Ubuntu 8.10 and I attached a webcam which on doing "lsusb" on my laptop gave the result - 

[B]Bus 007 Device 004: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100
[/B]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


But the /dev/video* gives only video0 as output which corresponds to the internal webcam.

even cheese is not able to run it.

I think the driver that it works with "gspca" is not installed or I accidently removed it.

I'm really stuck with this problem and would greatly appreciate your help.

Thank you in advance.:)

---

### Post by buntu_hugenewbie11 on 2009-09-19
Did you ever get this working?

---

