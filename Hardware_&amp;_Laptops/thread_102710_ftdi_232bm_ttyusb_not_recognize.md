---
title: "ftdi 232bm ttyusb not recognize"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by cory lee on 2005-12-12
how to tell what usb port or com (rs232) port the ftdi rs232bm chip is on? with windows drivers it detects it and tell what com port it is using such as com4 , com 9, etc..... linux problem?

did a lsusb as shown

cory@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 007: ID 0403:dc00 Future Technology Devices International, Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

also dmesg

[4317006.892000] usb 3-2: new full speed USB device using uhci_hcd and address 7
[4317071.996000] usbcore: registered new driver usbserial
[4317071.998000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
[4317072.000000] usbcore: registered new driver usbserial_generic
[4317072.000000] drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
[4317072.035000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI SIO
[4317072.037000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI 8U232AM Compatible
[4317072.041000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI FT232BM Compatible
[4317072.045000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI FT2232C Compatible
[4317072.072000] drivers/usb/serial/usb-serial.c: USB Serial support registered for USB-UIRT Infrared Tranceiver
[4317072.075000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Home-Electronics TIRA-1 IR Transceiver
[4317072.087000] usbcore: registered new driver ftdi_sio

---

