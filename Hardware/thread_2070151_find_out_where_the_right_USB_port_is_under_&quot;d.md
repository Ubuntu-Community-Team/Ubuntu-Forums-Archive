---
title: "find out where the right USB port is under &quot;/dev&quot; on my system"
date: 2012-10-12
forum: Hardware
---

### Post by swapnak on 2012-10-12
Hi,

I connected my device using usb cable to pc but iam not getting to which serial port my device is connected in /dev/tty*
i also tried mrdrobe command
sudo modprobe usbserial vendor=0x091e product=0x0003 and check again dmesg.
  but of no use?

Any help would be appreciated.
Thanks in advance
swapna

---

### Post by drmrgd on 2012-10-12
So, when you connect the device and check dmesg, you don't see anything come up in the output?  Usually, when you connect the device, if it's recognized and working, there will be output in dmesg that should show where it's being mapped.  What kind of device is it, and are you sure it's working correctly?

---

### Post by swapnak on 2012-10-12
HI drmrgd
Thanks for the reply.
The device is motorola droid. The same device i tested in windows it worked properly.

---

