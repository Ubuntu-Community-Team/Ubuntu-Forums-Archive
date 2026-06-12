---
title: "efax-gtk can't find modem"
date: 2012-10-27
forum: Hardware
---

### Post by RogerDavis on 2012-10-27
Modem is USR V.90 / V.92 Model 5610C Performance Pro Modem, using all standard command sets - INTERNAL, NOT WINMODEM!!!

sudo lspci gets the below modem info:
06:02.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)

It has worked before in this same setup, but after some system or other updates it quit working.

I get the following error info:
Socket running on port 9900
efax-0.9a: 01:11:06 Error: can't open serial port /dev/ttyS1: Permission denied
efax-0.9a: 01:11:06 failed page /home/roger/Documents/Libre Office/Saddleback Labs Request.pdf.001
efax-0.9a: 01:11:06 finished - unrecoverable error

If I try to send a fax, the indicator box in the lower left corner changes very briefly from "Inactive" to "Sending Fax", and then instantly back to "Inactive".  There is NO sound of off hook or dialing from the modem.

If I run it using sudo, it works!!!!!

Windows 7 finds the modem and sends faxes just fine, so the modem is fine.

How do I fix these problems?

---

### Post by RogerDavis on 2012-10-27
I tried to give myself permission to dial out, now I get:

Socket running on port 9900
efax-0.9a: 02:23:07 opened /dev/ttyS1
efax-0.9a: 02:23:07 failed page /home/roger/Documents/Libre Office/Saddleback Labs Request.pdf.001
efax-0.9a: 02:23:07 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:07 Error: fax device write: Input/output error
efax-0.9a: 02:23:09 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:11 Error: fax device write: Input/output error
efax-0.9a: 02:23:13 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:13 sync: dropping DTR
efax-0.9a: 02:23:13 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:14 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:16 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 sync: sending escapes
efax-0.9a: 02:23:18 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:19 Error: fax device write: Input/output error
efax-0.9a: 02:23:21 Error: fax device write: Input/output error
efax-0.9a: 02:23:23 Error: sync: modem not responding
efax-0.9a: 02:23:23 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:23 finished - unrecoverable error

And now sudo from terminal doesn't run it successfully

---

### Post by gv1899 on 2013-04-06
Same problems.

After give myself permission to dial out, also updated serial in efax-gtk/file/settings/modem/serial device, from "ttyS1" to "ttyS0".
This is because my modem is connected to the serial port 0, while the original configuration of efax-gtk was set to the serial 1.

Now it works.

---

