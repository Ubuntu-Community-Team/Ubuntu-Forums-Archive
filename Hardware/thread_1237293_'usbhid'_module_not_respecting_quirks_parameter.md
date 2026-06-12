---
title: "'usbhid' module not respecting quirks parameter?"
date: 2009-08-11
forum: Hardware
---

### Post by timbo_ on 2009-08-11
Hello,
I have a USB device (a Labjack U12, see [http://www.labjack.com]("http://www.labjack.com/")) which comes with its own kernel module.  However by default the 'usbhid' module claims it, preventing the correct driver module from working.  In Ubuntu 8.10 it was possible to fix this by setting the 'quirks' parameter to tell usbhid to ignore this particular device:

> $ cat /etc/modprobe.d/labjack.conf 
# Exception for Labjack driver
options usbhid quirks=0x0cd5:0x0001:0x0004


However in Ubuntu 9.04 (with kernel 2.6.28-14-generic) the usbhid module seems to be ignoring the quirks option.  'modprobe -v usbhid' shows that the options line is being picked up correctly, but 'dmesg' shows that usbhid is claiming the device anyway.

Any thoughts welcome,
Tim

---

### Post by Ron Snijders on 2009-10-02
To fix it I had to load the labjack module *before* the usbhid module:
- blacklist usbhid by adding the following line to /etc/modprobe.d/blacklist.conf
```
blacklist usbhid
```
- Add the following 2 lines to /etc/modules:
```
labjack
usbhid
```
- That's it!

Is there a better (cleaner) to do the above?

---

