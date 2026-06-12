---
title: "Ubuntu+USB radio AverMedia MR800"
date: 2009-05-27
forum: Hardware
---

### Post by gmann1 on 2009-05-27
Hi,

i have problem in Ubuntu 8.04 with usb radio AverMedia 800.
Ubuntu detect this "card" :

[I]
root@nos1-nb02:/home/milos# lsusb
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 002: ID 07ca:b800 AVerMedia Technologies, Inc.
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 002: ID 0458:0046 KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 03f0:171d Hewlett-Packard
Bus 001 Device 001: ID 0000:0000 


root@nos1-nb02:/home/milos# cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: No such file or directory
[/I]

- i installed gnome radio, but that's all :(

Can me anybody help with this problem ?
(clear and simple, step by step installation procedure) :)

Thx.

---

### Post by Alexey Klimov on 2009-05-31
> **gmann1 said:**
> Hi,

i have problem in Ubuntu 8.04 with usb radio AverMedia 800.
Ubuntu detect this "card" :

[I]
root@nos1-nb02:/home/milos# lsusb
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 002: ID 07ca:b800 AVerMedia Technologies, Inc.
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 002: ID 0458:0046 KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 03f0:171d Hewlett-Packard
Bus 001 Device 001: ID 0000:0000 


root@nos1-nb02:/home/milos# cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: No such file or directory
[/I]

- i installed gnome radio, but that's all :(

Can me anybody help with this problem ?
(clear and simple, step by step installation procedure) :)

Thx.

Hello,

Well, is gnomeradio works for you?

You can look in dmesg log typing "dmesg" in console/terminal. For example, i see such strings:

usbcore: registered new interface driver radio-mr800
radio_mr800: version 0.11 AverMedia MR 800 USB FM radio driver

That means that VideoForLinux driver for that radio loaded fine. If all is fine here, try to find file radio0, or radio1 (or radio2, etc) in /dev directory. This file you have to set in gnomeradio settings. (Probably, default is /dev/radio. Without number. You should set right file.)

If gnomeradio finds this file it should start works ok.

---

### Post by gmann1 on 2009-06-01
after dmesg a got output :

[I]
.
.
.
[ 6024.362694] hiddev96hidraw1: USB HID v1.10 Device [AVerMedia Technologies AVerMedia USB Radio] on usb-0000:00:1d.2-1
[/I]

I've tried dev for gnomeradio - /dev/usb/hiddev0 and the gnome radio start withou error msg, but no voice, nothing ...


That's all :(

---

