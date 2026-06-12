---
title: "Canon PIXMA iP2600 printer driver for Ubuntu 18.04"
date: 2020-09-23
forum: Hardware
---

### Post by welshmike on 2020-09-23
My apologies re this old printer. I picked up a cheap laptop recently that is running WIndows 10 and the driver supplied with the Canon printer works OK there.

I managed to get the printer working some years ago on an earlier release of Ubuntu, 14.04
At that time this was helpful but has not helped today:
[http://ubuntuhandbook.org/index.php/2014/12/canon-driver-scangear-mp-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/12/canon-driver-scangear-mp-ubuntu-14-04/)
.
Please is there a way of getting the printer to work on my main laptop that runs Ubuntu 18.04?

---

### Post by dino99 on 2020-09-23
You have to know if that hardware is found and well identified by the system:
- power it up
- glance at System Settings -> printers

lsusb output should list it. Ubuntu install should have already installed the required driver (system-config-printer-udev). Check you have ipp-usb installed (via synaptic for example)
Then you can glance at 'journalctl -b' to find related 'printer' 'usb' error/warning
 [https://www.linuxquestions.org/questions/linux-newbie-8/where-to-find-driver-to-canon-pixma-ip2600-to-work-in-ubuntu-859626/](https://www.linuxquestions.org/questions/linux-newbie-8/where-to-find-driver-to-canon-pixma-ip2600-to-work-in-ubuntu-859626/)

---

### Post by slickymaster on 2020-09-23
*Thread moved to **Hardware**.*

---

### Post by kurt18947 on 2020-09-24
I have no experience with Canon printers so take that into consideration. I would follow Dino99's advice. If that doesn't work, Canon does offer Linux support though it may be less obvious than Windows. A quick search brings up this:

[https://www.canon-europe.com/support/consumer_products/operating_system_information/](https://www.canon-europe.com/support/consumer_products/operating_system_information/)

Manufacturer support for linux does seem better in Europe and Asian than it seems in N. America. Do be a little careful about following random instructions found on the internet. Some will have you tieing your system into knots then leave you hanging or worse.

---

