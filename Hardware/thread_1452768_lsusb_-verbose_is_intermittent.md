---
title: "lsusb -verbose is intermittent"
date: 2010-04-12
forum: Hardware
---

### Post by ppeterb on 2010-04-12
I have several USB flash drives of various makes.  All are working well (mostly as bootable live 9.10 systems) so the USB drives are not the issue.  I can mount and unmount the devices, and read and write files, without any concern.

For good reason I want to know during runtime the device serial number (part of the inquiry information) and lsusb reports that as part of the -v verbose option.  The problem is that sometimes lsusb gives me a serial number and sometimes the field is blank.  I have not found a pattern or combination to get consistent or predictable results.  When the serial number is reported it is correct.

Is anyone else using lsusb in this manner?

It looks like the code for lsusb has not been touched in long time and the author named in man is (I'm sure) long gone from the Swiss lab.

(I have of course tried usbview but for whatever reason 9.10 does not support it.)

Peter

---

