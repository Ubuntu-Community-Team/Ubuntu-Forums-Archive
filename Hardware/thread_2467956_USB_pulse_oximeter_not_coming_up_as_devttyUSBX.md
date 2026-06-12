---
title: "USB pulse oximeter not coming up as /dev/ttyUSBX"
date: 2021-10-13
forum: Hardware
---

### Post by paulstaf on 2021-10-13
I recently purchased a Contec CMS50F pulse oximeter.

When I connect it to the USB port, lsusb shows it as:

Bus 003 Device 014: ID 28e9:028a

but it won't come up as a serial device such as: /dev/ttyUSBX which is what I need for the OSCAR software.

Older versions of this oximeter would work with a CP210X driver, and when I connect it to Windows, that is the driver it seems to be using, but it doesn't come up in Ubuntu 20.04, even though the driver is loaded:

$ lsmod | grep -i cp210
cp210x 36864 0
usbserial 53248 1 cp210x

I found an obscure post where someone said to create a udev rule to change the mode to 0666, I tried that, but it didn't work.

The OSCAR forum just says that the new version of the device firmware doesn't work, which nothing works until someone gets it to work, so I am hoping that someone out there who is really good with hardware/software can help me get it to come up as a serial device. It would be helping a lot of other people in the CPAP community who use linux exclusively as well.

Thanks in advance,
Paul

---

