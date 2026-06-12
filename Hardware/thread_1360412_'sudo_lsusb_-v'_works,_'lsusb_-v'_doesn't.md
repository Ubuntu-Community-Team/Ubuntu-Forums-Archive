---
title: "'sudo lsusb -v' works, 'lsusb -v' doesn't"
date: 2009-12-20
forum: Hardware
---

### Post by gregben on 2009-12-20
(Ubuntu 9.10 desktop x86 32 bit)

I have a specialized USB device (Opal-Kelly FPGA module)
that I can see if I run lsusb as a regular user:

$ lsusb 
...
Bus 002 Device 003: ID 151f:0022 Opal-Kelly XEM-3010 FPGA module
...

but, if I do:

$ lsusb -s 2:3 -v

I get:

...
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

at the end of the listing.

$ sudo lsusb -s 2:3 -v

works fine. (no Operation not permitted messages)
When running programs that attempt to interact with the
USB device, the device is not seen/recognized when running
as a regular user. When I repeat using sudo, the programs work correctly.

I'm thinking this has to do with /proc/bus/usb permissions
and/or hal, but I'm not sure.

Any help appreciated.

---

### Post by bboston7 on 2009-12-21
This is normal, just run the command with sudo.

---

### Post by gregben on 2009-12-21
> This is normal, just run the command with sudo.

No, it isn't. I have another machine running 9.10 and the 
programs (written in C++ and Python) that interact with the
USB device all work properly without sudo on it. 

Problem is I don't remember what I did on that machine to get it working properly, aside perhaps from installing Virtualbox which passes USB access through to the virtual machine.

---

### Post by Dark_Stang on 2009-12-21
Actually that is normal.

---

### Post by gregben on 2009-12-21
No, it is not normal.
I solved the problem.

The solution is to put a properly formatted file in /etc/udev/rules.d

In my particular case:

/etc/udev/rules.d/60-opalkelly.rules

which contains:

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="151f", MODE="0666"
SUBSYSTEM=="usb", ATTRS{idVendor}=="151f", MODE="0666"

Once this system is rebooted, lsusb -v works properly. No
error messages are generated. My programs interact with the USB
device correctly as well; no sudo required.

---

