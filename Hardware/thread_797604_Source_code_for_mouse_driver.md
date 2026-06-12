---
title: "Source code for mouse driver"
date: 2008-05-17
forum: Hardware
---

### Post by frederick1978 on 2008-05-17
Hello,

I am trying to write some usb drivers for ubuntu, and, as an example,  I would like to see the source code of the mouse that I've currently installed.

When I plug the mouse, a file named mouse1 is created in the folder /dev/input, when typing lsusb i get

Bus 002 Device 008: ID 0461:4d15 Primax Electronics, Ltd 

and with dmesg I get

[946616.715505] usb 2-6: USB disconnect, address 8
[946627.550981] usb 2-6: new low speed USB device using ohci_hcd and address 9
[946627.760150] usb 2-6: configuration #1 chosen from 1 choice
[946627.779294] input: USB Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input9
[946627.810827] input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:0b.0-6


Now,
1. how do I find which is the driver file (.ko) that is currently accessing the mouse1 file?

2. where can i find the source code for such driver?

3. why all the header files in /usr/src/linux-headers-2.6.24-16-generic/include/config/mouse/ are empty?


Thanks a lot for your time and for your help

          Kind regards

                  Federico

---

### Post by lemming465 on 2008-05-17
Run *lsmod* to see what modules are loaded.  One or more will be running your mouse.

Install the *linux-source* package to see what the code is.

---

### Post by rohit33 on 2011-04-13
not able to view the source code of anythng, pls help.

i have installed the linux-source package.

what shud i do after installing the package?
pls brief as im new to ubuntu


thanks

---

