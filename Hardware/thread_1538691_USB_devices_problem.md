---
title: "USB devices problem"
date: 2010-07-25
forum: Hardware
---

### Post by ben72 on 2010-07-25
I have 3 USB devices connected which are part of a cash register.

I need to know which ttyUSB* each device gets. I solved this with a udev rules files with symlinks to ttyS* which works fine.

The ttyS30 device does not work with the common lucid kernel. So I had to get the latest generic kernel, else it just does not work at all.

My only problem now is that the device that should come up as ttyS30 sometimes does not map to any ttyUSB* and hence the ttyS30 symlink points to bus something instead of ttyUSB* and the device is unusable. If I don't connect the ttyS10 device this is not a problem so it seems there is some kind of clash that sometimes prevents the ttyS30 device from working.

My rules are as follows:
[http://paste.ubuntu.com/468897/](http://paste.ubuntu.com/468897/)

When it works it looks like this:
[http://paste.ubuntu.com/468881/](http://paste.ubuntu.com/468881/)

When it does not work it looks like this:
[http://paste.ubuntu.com/468882/](http://paste.ubuntu.com/468882/)

Note the line:
util_run_program: '/sbin/modprobe' (stderr) 'FATAL: Module usb:v0519p0007d0400dc00dsc00dp00icFFiscFFipFF not found.'

I tried changing the rules file to only using idVendor as unique selection and it seemed to work at first but now it's the same again. Sometimes it works, sometimes it does not when starting up the computer.

It does always work it seems if plugging the ttyS10 device after startup of the computer. Then everything works.

One side problem is that this line never works:
ATTRS{idVendor}=="0519", ATTRS{idProduct}=="0007", RUN+="/bin/stty -F /dev/ttyS30 19200"


Thanks for any help in this matter! It would be fantastic if Ubuntu would work better as a POS system.

---

