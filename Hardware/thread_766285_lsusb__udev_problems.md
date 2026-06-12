---
title: "lsusb / udev problems"
date: 2008-04-25
forum: Hardware
---

### Post by MaartenLont on 2008-04-25
Hello,

I hope I post this in the right forum.

I have Ubuntu installed on a new HP pavilion laptop and it works perfect. I'm now trying to program my Spartan3E starterkit (FPGA). I had to install new Firmware and driver (libusb-driver.so) this seems to work OK.

But, i'm trying to list the usb devices with "lsusb" and it just hangs without an error message (how long should I wait?). When I try to restart udev (needed to load the new driver rules?) using "sudo /etc/init.d/udev restart" it takes a long time and then it fails.

Is it normal that restarting udev fails? And why does lsusb not work?

Thanks in advance,
Maarten

---

