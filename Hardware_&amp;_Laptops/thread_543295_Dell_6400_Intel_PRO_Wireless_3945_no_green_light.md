---
title: "Dell 6400 Intel PRO Wireless 3945 no green light"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by doubleDog on 2007-09-04
I have read many posts about this here and on LinuxQuestions.org -- perhaps if I knew more I could read between the lines and *get it,* but... I don't  :confused:

I installed the 7.04 server, then the desktop, then (with the help of the this forum) configured the ATI Radeon X1400 (1280 x 800). However the wireless card (indicator) does not light up. It's not the radio switch, I have checked the hardware setup (F2 during boot) -- and everything is turned on -- the blue light for bluetooth comes on.

Using the command: sudo dmseg|grep 3945 yields:
ipw3945: Intel (R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
ipw3945: Copyright(c) 2003-2006 Intel Corporation
ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection

Using iwconfig yields:
lo    no wireless extensions.

eth0  no wireless extensions.

Thanks for reading -- please point me to something a noob can follow.

---

### Post by matthedane on 2007-09-23
Hi

Try this command
sudo modprobe fsam7400 radio=1

I might solve the problem...

Matt

---

