---
title: "Run command on pluging in usb modem"
date: 2011-01-16
forum: Hardware
---

### Post by sandeepthakurala on 2011-01-16
Hi,

I have a usb modem and to use that usb modem I have to run following command on terminal each time I plugin the modem to use it. Now I want a way so that whenever I plugin the modem this command should fire automtically.

Command : sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1:1446

Please help me. I am new user to ubuntu.

Thanks.

---

### Post by IcarusR on 2011-01-16
This can be done by writing a udev rule.
Info on writing rules here..

[http://www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html")

---

