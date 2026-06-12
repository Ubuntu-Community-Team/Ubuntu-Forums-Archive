---
title: "Agere Dial up USB Modem Needs help"
date: 2009-02-04
forum: Hardware
---

### Post by odzk on 2009-02-04
Hi guys, i have a usb dial up modem that i want to use. ubuntu detected the modem but the problem is gnome ppp doesn detect that there is a dial up modem installed.

in the terminal i type lsusb, and this is what ive got

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 001 Device 006: ID 047e:2892 Agere Systems, Inc. (Lucent) Systems Soft Modem[/COLOR]
Bus 001 Device 003: ID 0cf2:6225 ENE Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can anyone please help me, i dont want to reinstall windows xp.

---

### Post by ModelM on 2009-02-04
The words "soft modem" are the giveaway here. This is a "winmodem" and it won't work without drivers. Hardware modems work by just connecting them, but winmodems require drivers.

The USR5637 is an example of a USB hardware modem - you just plug it in & use it.

I don't know where to find the driver for your modem, but at least now you know what's required.

---

