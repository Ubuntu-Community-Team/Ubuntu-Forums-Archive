---
title: "[SOLVED] Hardward detection"
date: 2008-12-16
forum: Hardware
---

### Post by unknown user on 2008-12-16
How can I detect a usb piece of hardware that is not being detected by ubuntu?

---

### Post by taurus on 2008-12-16
Maybe with the lsusb command.

---

### Post by unknown user on 2008-12-16
what do I do with this just enter it into the terminal and press return?

---

### Post by doobiest on 2008-12-16
yes:

doobiest@LinuxBox:/etc/apache2$ lsusb
Bus 002 Device 006: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 002 Device 005: ID 046d:c041 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 002 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


similarly lspci will list pci devices.

---

### Post by unknown user on 2008-12-16
I think it might be OK and the devise will work in ubuntu as this is my results:

unknown@unknown-laptop:~$ lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 007: ID 6993:b001 Freshtel FT-102 VoIP USB Phone

Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 002: ID 413c:3016 Dell Computer Corp. 

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

unknown@unknown-laptop:~$ sudo install Freshtel FT-102 VoIP USB Phone

[sudo] password for unknown: 

install: target `Phone' is not a directory

unknown@unknown-laptop:~$ cat /proc/asound/cards

 0 [ICH6           ]: ICH4 - Intel ICH6

                      Intel ICH6 with AD1981B at irq 21

 1 [default        ]: USB-Audio - VOIP USB Phone           

                      Yealink Network Technology Ltd. VOIP USB Phone            at usb-0000:00:1d.1-1

---

### Post by taurus on 2008-12-16
> **unknown user said:**
> I think it might be OK and the devise will work in ubuntu as this is my results:

unknown@unknown-laptop:~$ lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 007: ID 6993:b001 Freshtel FT-102 VoIP USB Phone

Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 002: ID 413c:3016 Dell Computer Corp. 

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

unknown@unknown-laptop:~$ **[COLOR="Blue"]sudo install Freshtel FT-102 VoIP USB Phone[/COLOR]**

[sudo] password for unknown: 

install: target `Phone' is not a directory

unknown@unknown-laptop:~$ cat /proc/asound/cards

 0 [ICH6           ]: ICH4 - Intel ICH6

                      Intel ICH6 with AD1981B at irq 21

 1 [default        ]: USB-Audio - VOIP USB Phone           

                      Yealink Network Technology Ltd. VOIP USB Phone            at usb-0000:00:1d.1-1

I have no idea what you are trying to do there?

---

### Post by unknown user on 2008-12-16
lol sorry that was me just messing around, thought that drivers may of been needed.

This started with my not being able to set up my internet phone and thinking that ubuntu could not detect the usb unit, but I think it looks like it has.

---

### Post by unknown user on 2008-12-17
Due to the fact that it looks like my system has detected the usb phone, it just seems that the phone needs to be set up correct. Thanks for your help, closing this thread.

---

