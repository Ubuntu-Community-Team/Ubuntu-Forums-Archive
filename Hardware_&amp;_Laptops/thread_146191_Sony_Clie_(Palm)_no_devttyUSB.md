---
title: "Sony Clie (Palm) no /dev/ttyUSB*"
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by pksings on 2006-03-17
Last week this worked fine, this week after a kernel update, it does not.

 2.6.12-10-686 is the kernel version.  I have not tried a different kernel yet.

This week it does not recognize the device and insert the "visor" module and generate the "udev" devices.

Upon manual insertion of "visor" module the following shows up in /var/log/messages. Without manual insertion of module only the failure messages appear.  This represents repeated insertions in all the different USB ports.  

[4323987.175000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver v2.1
[4324276.810000] usb 2-1: new full speed USB device using uhci_hcd and address 14
[4324276.884000] usb 2-1: device descriptor read/64, error -71
[4324277.059000] usb 2-1: device descriptor read/64, error -71
[4324277.222000] usb 2-1: new full speed USB device using uhci_hcd and address 15
[4324277.296000] usb 2-1: device descriptor read/64, error -71
[4324277.472000] usb 2-1: device descriptor read/64, error -71
[4324277.637000] usb 2-1: new full speed USB device using uhci_hcd and address 16
[4324278.047000] usb 2-1: device not accepting address 16, error -71
[4324278.109000] usb 2-1: new full speed USB device using uhci_hcd and address 17
[4324278.525000] usb 2-1: device not accepting address 17, error -71


I have no idea how to troubleshoot this..

---

