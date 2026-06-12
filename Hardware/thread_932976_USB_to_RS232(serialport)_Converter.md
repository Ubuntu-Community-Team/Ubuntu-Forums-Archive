---
title: "USB to RS232(serialport) Converter"
date: 2008-09-29
forum: Hardware
---

### Post by L4S7 on 2008-09-29
I recently bought a USB to RS232 Converter, just having a few issues getting the drivers going.

It came with a driver disk, made for windows.

on the driver disk it does have a LINUX folder. the files in the folder are labeled.

ftfi_sio.c    ftdi.sio.h  makefile   Rules.make


im not to sure if i need to use those to get the drivers for Ubuntu.

Ive found a few post that explained a bit on installing drivers but i couldnt get it to work for me.

I did do a dmesg to check the port

```
[  296.167622] usb 4-2 FTDI USB Serial Device Converter now attached to ttyUSB0
```

so must know its there.

When i try to use the serial port it just says "no usable serial ports found"

---

