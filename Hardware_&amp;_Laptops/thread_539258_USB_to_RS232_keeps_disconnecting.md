---
title: "USB to RS232 keeps disconnecting"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by Ne0z on 2007-08-31
Hi , i'm trying to connect to a device using a USB to RS232 converter to debug it throught minicom. 
However the device does not communicate properly and hangs up in minicom 

and when i check thru "dmesg" , it says that my USB to RS232 converter was connected and then disconnected as follows

[ 6079.452000] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 6079.452000] drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[ 6079.452000] usb 2-1: FTDI USB Serial Device converter now attached to
ttyUSB0
[ 6079.776000] usb 2-1: usbfs: interface 0 claimed by ftdi_sio while
'brltty' sets config #1
[ 6079.776000] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now
disconnected from ttyUSB0
[ 6079.776000] ftdi_sio 2-1:1.0: device disconnected

can anyone help me out ? thanks heaps !:)

---

### Post by ramjet_1953 on 2007-08-31
Often, problems with USB to Serial are associated with a package that is loaded by default called Brltty.

Brltty is a package for the blind and is used with Braille readers.

If you remove this package, hopefully, things should work.

[COLOR="Red"]sudo apt-get remove brltty

sudo apt-get remove brltty-x11[/COLOR]

Regards,
Roger :cool:

---

### Post by Thomas Pips on 2007-09-11
This solution works!

Thank you very much!

---

### Post by RFScheer on 2007-10-23
Also worked for me - thanks! - Robert

---

