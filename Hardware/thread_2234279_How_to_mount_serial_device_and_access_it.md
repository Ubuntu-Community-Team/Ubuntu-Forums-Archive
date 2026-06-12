---
title: "How to mount serial device and access it?"
date: 2014-07-13
forum: Hardware
---

### Post by thexnightmare on 2014-07-13
Dear,
I ve plugged an accelometer device through usb to a ubuntu machine.
And i found in dev/serial/byid/the name of it
and ive installed a serial terminal, however when i trying to connect through serial terminal it show me /dev/ttys0 option.
but cant connect.
Any idea how to connect to it and see the values of the accelometer?

Note:
In windows, I just plug the device, and windows give it address COM11.
And through a terminal, I connect to COM11 and see the data from it.

---

### Post by kd5mkv on 2014-07-13
open terminal $ dmesg | grep tty 

will show your serial ports also you need to check to see if you have dialout permission, 

sudo addgroup $USERNAME dialout

Noticed recently serial port dialout wasn't running on default, so permission is required. Maybe this will give you a start!

---

