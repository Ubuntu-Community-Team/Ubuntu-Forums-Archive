---
title: "FTDI on Linux for USB to RS-485 comm"
date: 2015-11-12
forum: Hardware
---

### Post by mihai5 on 2015-11-12
Hi,

I am fairly new to Linux and am running Ubuntu 14.04.  I am trying to use a USB to RS-485 converter: [http://www.iocrest.com/en/product_details431.html](http://www.iocrest.com/en/product_details431.html)
I followed the instructions on installing the driver: [http://www.ftdichip.com/Support/Documents/AppNotes/AN_220_FTDI_Drivers_Installation_Guide_for_Linux%20.pdf](http://www.ftdichip.com/Support/Documents/AppNotes/AN_220_FTDI_Drivers_Installation_Guide_for_Linux%20.pdf)

But how do I actually configure the RS-485 settings and send/receive data?

You help is really appreciated.

Thanks!

---

### Post by blm-ubunet on 2015-11-13
Add your "user" to the "dialout" group.
The common FTDI & Parallax devices have kernel support.

Remove/plugin the USB adaptor.
run "dmesg"
or
```
dmesg | grep -i 'tty\|USB' > logging.txt
```

Could post as attachment?

Config baud rate etc:
setserial
stty -F /dev/ttyUSB0 19200
could have to change permissions
```
chmod 777 /dev/ttyUSB0
```
Note: ttyUSB0 could be different number.


Can send data with "cat" or an actual terminal program..
[http://unix.stackexchange.com/questions/42964/unexpected-results-testing-serial-loopback-using-echo-and-cat](http://unix.stackexchange.com/questions/42964/unexpected-results-testing-serial-loopback-using-echo-and-cat)

---

