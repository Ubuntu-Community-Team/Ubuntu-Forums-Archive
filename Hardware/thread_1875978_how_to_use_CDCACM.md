---
title: "how to use CDC/ACM"
date: 2011-11-05
forum: Hardware
---

### Post by mistertransistor on 2011-11-05
I have an I2C device (an ADC) that I'm attaching to 11.04 using an I2C-USB converter that provides a CDC/ACM interface, although it's obviously not a modem. When I plug it in, /dev/ttyACM0 appears. However, rxtx does not show that device in the list of serial ports. If I hard-code it and try to open it, I get an IO exception.

I can communicate with it, sometimes, by adding the appropriate usbserial line in /etc/modules, which creates /dev/ttyUSB0, which *is* listed by rxtx and usually does work, although dmesg shows an error that it is not a bulk device. However, rxtx sometimes just hangs mysteriously on port opening.

What's the correct way to use this device? Why does rxtx not handle ttyACM0? I did see workarounds on the Web that involve symlinking to ttyS9 (say), but that did not seem to work for me.

Thanks for any advice, general or specific, on the right way to use ttyACM0.

---

