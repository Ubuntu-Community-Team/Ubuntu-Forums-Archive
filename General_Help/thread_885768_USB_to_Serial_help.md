---
title: "USB to Serial help"
date: 2008-08-10
forum: General Help
---

### Post by Charlie708 on 2008-08-10
I have an FT232BM based USB to serial converter, and cannot figure out how to get it to work.  The device is sucessfully recognized by the system, is attached to ttyUSB0, and I have removed the brltty packages.

Output of dmesg:
> 
[ 1262.359656] usb 2-1: new full speed USB device using ohci_hcd and address 12
[ 1262.449323] usb 2-1: configuration #1 chosen from 1 choice
[ 1262.470404] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 1262.470442] /build/buildd/linux-2.6.24/drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[ 1262.470515] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0


The device on lsusb:
> 
Bus 002 Device 012: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC


I am new to using USB to serial converters, and am not sure how to use it.  The software I am trying use is Powercommander software for high performance motorcycle parts, and works great under wine.  My only gripe is that the powercommander software expects the module in the bike on a physical serial port, so the options range fro COM1-COM8.  Is there anyway I can get this working under Linux?  I have a copy of Windows installed right now, but don't want to dual boot just for this software.

---

### Post by Mister.Vash on 2008-08-10
Try something like the following before starting wine

sudo ln -sb /dev/ttyUSB0 /dev/ttyS2

That creates a link from to COM3 that wine can use.  If you already have that serial port in use, you might try a higher number like

sudo ln -sb /dev/ttyUSB0 /dev/ttyS4

This isn't persistent across reboots, so if it works, you may want to create a script that does this then launches your wine application

---

### Post by Charlie708 on 2008-08-10
That is exactly what I was trying to do, thanks!

I just tested this out, and it works perfectly.  The powercommander software detected the presence of the module right away, and it loaded all my maps perfectly.  Double thanks!

---

