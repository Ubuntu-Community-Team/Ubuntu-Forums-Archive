---
title: "Which USB device is connected to which USB port?"
date: 2012-11-21
forum: Hardware
---

### Post by boondocks on 2012-11-21
This older PC has 3 USB 1.1 ports and 1 USB 2.0 port.
There 1 USB keyboard and 1 USB webcam connected to this PC.
Currently, I have only ssh access to this PC.

How do you find out which device is connected to which port? (From the command line.)

I want to make sure that the USB keyboard is connected to any one of the USB 1.1 ports.
And the USB webcam is connected to the only USB 2.0 port.

---

### Post by papibe on 2012-11-21
Hi boondocks.

Use this command to see what is connected to USB devices:
```
lsusb
```
For a more comprehensive results use the verbose option:
```
lsusb -v
```
That would be a long list with lots of details, so I would recommend redirecting it to a file, and then examine the file. For example:
```
lsusb -v > usbinfo.txt
```
Then under your device name, look for the field called 'bcdUSB'. That should tell you which version the device complies to (for instance 1.00, 2.00, etc).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by boondocks on 2012-11-21
Thanks papibe !  That was perfect.
I asked somebody at the PC to move the USB webcam to the USB 2.0 AND the additional benefit was that webcam is now running at a higher resolution 1280x720.
When it was connected to the USB 1.0 port, it would never go higher than 640x480.

---

### Post by papibe on 2012-11-22
:D very clever!

---

