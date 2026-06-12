---
title: "Device 'Hewlett-Packard lt4120 Snapdragon X5 LTE'"
date: 2021-12-09
forum: Hardware
---

### Post by nginmu on 2021-12-09
I suspect my  HP lt4120 wireless broadband card isn't working because of kernel issues. It doesn't like kernels equal to or above 5.9.14

I've identified and ordered a Sierra Wireless EM7345 card which hopefully *should* work with my kernel.

In the event this solution still doesn't work, could I ask if someone who is running Ubuntu (or a derivative) 21.04, or 21.10 with a Linux kernel equal to or above 5.9.14, and who has a working PCI Express M.2 75-pin Module, WWAN / mobile broadband card in their device, (mainly laptops and tablets I should think), let me know what card they've got so I can try and Ebay something that will work on my laptop and kernel.

I'll post back when the Sierra card comes, if it does or doesn't work.

Thanks!

---

### Post by nginmu on 2021-12-16
Sierra Wireless EM7345 card rejected by HP Elitebook 850 G3's BIOS: "unsupported WWAN card has been disabled".

HP list just one alternative card for this machine, but it's only 3G.

So it looks like I'm stuck with the HP LT4120 card.

but no matter - solution found:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574582](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574582)

The key part that fixed it for me is in reply #12:

> 
Update 2:
You can also correct the fault in qmi based old modem udev script by replacing line:
ATTR{bConfigurationValue}="1"
with
RUN+="/usr/sbin/usb_modeswitch -v 03f0 -p 9d1d --configuration 1"
and it works without qmi errors.
The direct write to attribute in udev script started to brake functionality from kernel 5.1x


It now works.

---

