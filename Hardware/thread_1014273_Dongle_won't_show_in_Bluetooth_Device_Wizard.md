---
title: "Dongle won't show in Bluetooth Device Wizard"
date: 2008-12-17
forum: Hardware
---

### Post by MikB on 2008-12-17
Hi,

I am using a fresh install of Ubuntu 8.10 based on the minimal iso image install followed by an apt-get install gnome.

OS is functioning fine but when I tried to install my bluetooth dongle with the Bluetooth Device Wizard nothing is listed in the "Select the device you want to setup" window, but the wizard icon is present in the taskbar showing that a device is ready to install.

I am using a Bluetooth v2.0 USB Dongle Class I through a USB hub (which worked fine in Windows XP).

I am hoping to use xgnokii to connect to my Nokia mobile phone but the programme hangs after a short while forcing a quit while trying to connect...

lsusb command gives the following result - see device 004

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can anyone help me to figure out this install problem?

Many thanks.

---

### Post by MikB on 2008-12-19
Update!

I've noticed when starting up the machinary that two messages are displayed before the gui kicks in

> usb 1-1 not accepting address 2 error -71

and something like

> hub 1:0 1:0 not enumberating device on port 1

Have tried plugging bluetooth dongle into another usb port rather than hub with same result - not detected in setup wizard.

Can anyone help me out?

---

### Post by Fire_Chief on 2008-12-23
Although my bluetooth adapter is built-in to my laptop, I've found the setup wizard is not for configuring your dongle but rather that's the wizard for detecting and pairing another bluetooth device (phone, mouse, keyboard, etc.). Perhaps Ubuntu is detecting and configuring your dongle automatically and you just need to try pairing with another device?

Cheers!

---

### Post by MikB on 2008-12-24
Oh yes... so it is.

:oops:

Thanks very much!

---

### Post by rokyman on 2009-03-15
thank you:o

---

