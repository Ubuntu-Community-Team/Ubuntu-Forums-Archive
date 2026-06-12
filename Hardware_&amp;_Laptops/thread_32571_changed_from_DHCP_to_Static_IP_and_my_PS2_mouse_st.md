---
title: "changed from DHCP to Static IP and my PS/2 mouse stopped working"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by TasKiNG on 2005-05-08
Hi,
 I have changed my networking from DHCP to Static IP. When I rebooted my PS/2 mouse had stopped working.( cursor would not move )
I have tried another mouse and get the same problem.

dmesg reports :-
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1

Any suggestions ?

It works ok with a usb mouse but the problem is really bugging me now

Cheers

Dave

---

### Post by alastair on 2005-05-08
Hard to believe that the nwtwork change had anything to do with this.

Show a little more /var/log/syslog (mouse relevant) plus the /etc/X11/xorg.conf file.

Plus, worth looking at the X logs (/var/log/Xorg.0.log).

---

### Post by crane on 2005-05-08
[QUOTE=alastair]Hard to believe that the nwtwork change had anything to do with this.

Show a little more /var/log/syslog (mouse relevant) plus the /etc/X11/xorg.conf file.

Plus, worth looking at the X logs (/var/log/Xorg.0.log).[/QUOTE]

I agree, very odd. have you rebooted again? If you change it back to dhcp does the problem go away?

---

