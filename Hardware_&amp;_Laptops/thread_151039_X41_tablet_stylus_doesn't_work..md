---
title: "X41 tablet stylus doesn't work."
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by djdial on 2006-03-27
System: Thinkpad X41T 1866 series

 I followed a previous thread..
 After installing the following packages:

    "wacom-kernel-source"
    "wacom-tools"
    "xserver-xorg-input-wacom",

I modified the "/etc/X11/xorg.conf" file in the inputdevice section and in the server layout section. And ran "setserial" like this:

    $ sudo setserial /dev/ttyS0 port 0x0200 irq 5 autoconfig

and then the command

    $ wacdump -f c100 /dev/ttyS0

gave a result which looked like something worked.
(and I attached the "setserial" command to the /etc/rc.local file.)
But as I re-login to X-window system, nothing worked with the stylus. What should I do?

---

