---
title: "Usb-Serial adapter"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by caguero on 2005-11-09
hi comunity,

someone has up and running an usb-serial adapter under ubuntu?
I need to buy some of these devices and I've not experience if it's fully supported under Ubuntu. 

Thanks in advance,
       Carlos

---

### Post by ranf on 2005-11-09
[QUOTE=caguero]hi comunity,

someone has up and running an usb-serial adapter under ubuntu?
I need to buy some of these devices and I've not experience if it's fully supported under Ubuntu. 

Thanks in advance,
       Carlos[/QUOTE]
I have one. 
When I plug it in `dmesg' tells me:
```

Nov 10 00:58:10 localhost kernel: [4306301.992000] usb 1-1.4: new full speed USB device using ohci_hcd and address 3
Nov 10 00:58:10 localhost kernel: [4306302.399000] usbcore: registered new driver usbserial
Nov 10 00:58:10 localhost kernel: [4306302.402000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
Nov 10 00:58:10 localhost kernel: [4306302.421000] usbcore: registered new driver usbserial_generic
Nov 10 00:58:10 localhost kernel: [4306302.421000] drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
Nov 10 00:58:10 localhost kernel: [4306302.461000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI SIO
Nov 10 00:58:10 localhost kernel: [4306302.464000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI 8U232AM Compatible
Nov 10 00:58:10 localhost kernel: [4306302.467000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI FT232BM Compatible
Nov 10 00:58:10 localhost kernel: [4306302.473000] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI FT2232C Compatible
Nov 10 00:58:11 localhost kernel: [4306302.482000] drivers/usb/serial/usb-serial.c: USB Serial support registered for USB-UIRT Infrared Tranceiver
Nov 10 00:58:11 localhost kernel: [4306302.490000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Home-Electronics TIRA-1 IR Transceiver
Nov 10 00:58:11 localhost kernel: [4306302.526000] ftdi_sio 1-1.4:1.0: FTDI 8U232AM Compatible converter detected
Nov 10 00:58:11 localhost kernel: [4306302.530000] usb 1-1.4: FTDI 8U232AM Compatible converter now attached to ttyUSB0
Nov 10 00:58:11 localhost kernel: [4306302.530000] usbcore: registered new driver ftdi_sio
Nov 10 00:58:11 localhost kernel: [4306302.530000] drivers/usb/serial/ftdi_sio.c: v1.4.2:USB FTDI Serial Converters Driver
Nov 10 00:58:11 localhost usb.agent[8261]:      ftdi_sio: loaded successfully

```
`lsusb' output:
```

Bus 001 Device 003: ID 0403:8372 Future Technology Devices International, Ltd FT8U100AX Serial Port

```
I use it with my serial GPS receiver.

---

### Post by ZooEyes on 2005-11-09
You'll just have to test. I have couple of those and my Suse & ubuntu 5.10 recognise these as;

--
Usb 1-1: new full speed USB device using uhci_hcd and address 7
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usbcore: registered new driver usbserial_generic
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
drivers/usb/serial/usb-serial.c: USB Serial support registered for MCT U232
mct_u232 1-1:1.0: MCT U232 converter detected
usb 1-1: MCT U232 converter now attached to ttyUSB0
usbcore: registered new driver mct_u232
drivers/usb/serial/mct_u232.c: Magic Control Technology USB-RS232 converter driver z2.0
--

This adapter is taiwan made, marked as U232-P9 - with no brand name. Another is Trendnet TU-S9 and it's detected as;

--
usb 1-1: new full speed USB device using uhci_hcd and address 8
drivers/usb/serial/usb-serial.c: USB Serial support registered for PL-2303
pl2303 1-1:1.0: PL-2303 converter detected
usb 1-1: PL-2303 converter now attached to ttyUSB0
usbcore: registered new driver pl2303
drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver v0.12
--

So, both of them are working..

---

### Post by caguero on 2005-11-14
We are going to try a pair of Trendnet. Thanks a lot!!

Carlos

---

