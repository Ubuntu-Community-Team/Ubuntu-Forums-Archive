---
title: "Rikaline GPS 6010 Drivers?"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by jadacyrus on 2006-02-09
On their website their linux drivers are only for Redhat7 to 9 and none of them compile under Ubuntu..  Has anyone got this GPS receiver working under ubuntu and can anyone point me in the right direction? Would really appreciate it thanks.

---

### Post by mips on 2006-02-09
Maybe they can be packaged as rpm's and then converted via alian. 

What errors do you get when you try to compile it ?

Can also have a look at [http://gpsd.berlios.de/](http://gpsd.berlios.de/)  might be in the repos.

---

### Post by jadacyrus on 2006-02-09
After I plug it in to my USB dmesg gives me this:

```
[5654894.547000] usb 1-1: new full speed USB device using uhci_hcd and address 2[5654895.446000] usbcore: registered new driver usbserial
[5654895.447000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
[5654895.449000] usbcore: registered new driver usbserial_generic
[5654895.450000] drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
[5654895.457000] drivers/usb/serial/usb-serial.c: USB Serial support registered for PL-2303
[5654895.460000] pl2303 1-1:1.0: PL-2303 converter detected
[5654895.483000] usb 1-1: PL-2303 converter now attached to ttyUSB0
[5654895.483000] usbcore: registered new driver pl2303
[5654895.483000] drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver v0.12

```

Which tells me that the drivers are already loaded.. I've been using gpsd however when used with gpsdrive or any other client software like xgps it says there aren't enoguh satellites or it doesn't get a fix. So I thought it was just my location, I drove around with that thing on top of my car for 20 minutes on a main highway and I still didn't get a fix.. No idea why this isnt working.

---

### Post by jadacyrus on 2006-02-09
More information..

when I run "gpsd -f /dev/ttyUSB0 -n -N" .. i get the following output:

```
This is normally a bug in some application using the D-BUS library.
24164: arguments to dbus_message_iter_append_basic() were incorrect, assertion "real->iter_type == DBUS_MESSAGE_ITER_TYPE_WRITER" failed in file dbus-message.c line 2125.
This is normally a bug in some application using the D-BUS library.
24164: arguments to dbus_message_iter_append_basic() were incorrect, assertion "real->iter_type == DBUS_MESSAGE_ITER_TYPE_WRITER" failed in file dbus-message.c line 2125.

```

Not sure what that means.

---

### Post by jadacyrus on 2006-02-09
Okay, I've made some progress... I got ONE lock and then nothing. I keep getting these messages: Unknown SiRF packet ...and then a bunch of numbers.. not sure

But at least a lock is good

---

### Post by jadacyrus on 2006-02-09
Okay nevermind i figured it out, finally got a good lock with gpsdrive, just had to leave it on for like 20 minutes..now its tiem to configure it with kismet.. hehehe

---

