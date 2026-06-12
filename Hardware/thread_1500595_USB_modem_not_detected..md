---
title: "USB modem not detected."
date: 2010-06-03
forum: Hardware
---

### Post by JimGvo on 2010-06-03
I have a radio modem that has a USB interface.  I'm trying to get it to 
communicate on Linux, but I get the following from dmesg when I plug it in:

[ 1946.015692] 
/build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial 
support registered for FTDI USB Serial Device
[ 1946.016324] usbcore: registered new interface driver ftdi_sio
[ 1946.016332] /build/buildd/linux-2.6.24/drivers/usb/serial/ftdi_sio.c: 
v1.4.3:USB FTDI Serial Converters Driver
[ 1961.529792] usb 1-1: new full speed USB device using ohci_hcd and 
address 6
[ 1963.030364] usb 1-1: configuration #1 chosen from 1 choice

In order to get that far I had to
  modprobe ftdi_sio

However it's not assigning a /dev entry to the device.  I know generic 
USB works OK since when I hook  up another device with a serial chip I 
get this in dmesg:

[ 3053.016750] usb 1-1: configuration #1 chosen from 1 choice
[ 3053.022463] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
[ 3053.022513] /build/buildd/linux-2.6.24/drivers/usb/serial/ftdi_sio.c: 
Detected FT232RL
[ 3053.022678] usb 1-1: FTDI USB Serial Device converter now attached to 
ttyUSB0

So what might I need to do to get this thing working?  I'm running 
Ubuntu 8.04.2 kernel 2.6.24-24-generic.

sudo lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 009: ID 0403:d010 Future Technology Devices 
International, Ltd
Bus 001 Device 001: ID 0000:0000

It becomes com6 on Windows, so I know the cable/modem are OK

If this isn't the right discussion group, please tell me where I should go.

Thanks,
Jim.

---

