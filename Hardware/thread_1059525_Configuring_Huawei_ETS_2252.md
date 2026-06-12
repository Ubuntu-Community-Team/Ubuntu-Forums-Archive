---
title: "Configuring Huawei ETS 2252"
date: 2009-02-03
forum: Hardware
---

### Post by rajeev3001 on 2009-02-03
i followed guide given in following link to install a Huawei ETS 2252 on Ubuntu 8.10
[http://installing-huawei-cdma-modem-in-linux.blogspot.com/](http://installing-huawei-cdma-modem-in-linux.blogspot.com/)

it says 'sudo dmesg -c' command should give the following error:
ti_usb_3410_5052 1-1:1.0: TI USB 3410 1 port adapter converter detected
ti_usb_3410_5052: probe of 1-1:1.0 failed with error -5

this seems to be with the usb to serial cable given with some ETS phones.

but the phone i'm using has a USB data cable. [usb port at phone instead of a serial port]
and when i type 'sudo dmesg -c' command after plugging it, it gives the following message:

[  373.848058] usb 2-1: new full speed USB device using uhci_hcd and address 7
[  374.072760] usb 2-1: configuration #1 chosen from 1 choice

according to the tutorial, we should configure 'vwdial' with:
Modem = /dev/ttyUSB0

but this device doesn't seem to be assigned to 'ttyUSB0' [as mentioned in tutorial]

the problem i've faced is, how can i configure this at 'vwdial'?

i'm a newcomer to ubuntu and your help will be much appreciated.

---

