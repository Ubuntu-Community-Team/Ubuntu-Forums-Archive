---
title: "Problem accessing /dev/ttyUSB0 immediately after startup"
date: 2011-07-20
forum: Hardware
---

### Post by vanster on 2011-07-20
Hi all,

I am having some trouble accessing /dev/ttyUSB0 which is a FTDI usb-to-serial converter (ftdi_sio kernel module) immediately after startup. Although dmesg shows that the device was registered (approx 3.5 seconds after kernel load) I still have to wait 20 seconds before I can open the /dev/ttyUSB0 device during which the device reports:

"/dev/ttyUSB0: Device or resource busy" 

I tried "lsof | grep ttyUSB0" to determine if any other processes are acessing the device after startup but no luck.

Has anyone encountered such behaviour?

Any suggestions as to how one may determine where the problem is?

Thank you in advance

Kind Regards
Pieter van Schaik

---

