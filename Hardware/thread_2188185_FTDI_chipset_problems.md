---
title: "FTDI chipset problems"
date: 2013-11-15
forum: Hardware
---

### Post by esclavosoy on 2013-11-15
I've got a USB-Serial converter with FTDI chip.  Items connected to it stop functioning.  I've done some searches and found some old results showing that there's some kind of bug.  But these are 2 year old post, I hope there's a fix now.

Does anyone have any ideas on a fix?

gmoreno@mofen:~$ lsmod |grep ftdi
ftdi_sio               40679  1 
usbserial              47113  3 ftdi_sio

gmoreno@mofen:~$ dmesg | grep FTDI
[   18.085676] USB Serial support registered for FTDI USB Serial Device
[   18.085827] ftdi_sio 6-1:1.0: FTDI USB Serial Device converter detected
[   18.090639] usb 6-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   18.090660] ftdi_sio 6-1:1.1: FTDI USB Serial Device converter detected
[   18.095236] usb 6-1: FTDI USB Serial Device converter now attached to ttyUSB1
[   18.095295] ftdi_sio: v1.6.0:USB FTDI Serial Converters Driver
[167007.715157] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[167007.723338] ftdi_sio ttyUSB1: FTDI USB Serial Device converter now disconnected from ttyUSB1



Thanks,

Gabriel

---

