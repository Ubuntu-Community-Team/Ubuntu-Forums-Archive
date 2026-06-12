---
title: "Bluetooth Restart Required after GDM, X, Screensaver"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by oliver.greg@gmail.com on 2007-07-29
I am running Feisty Fawn x86_64 with the following bluetooth..

Bus 001 Device 006: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth

My mouse:

Scanning ...
        00:07:61:6B:A0:26       Logitech MX1000 mouse
greg@greg-laptop:~$ sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services                                         [ OK 

Restarting bluetooth brings it back up at this point and it works.  I am running in HID mode..

Ok, upon boot, it works until GDM starts, then stops.  I can login to another tty, restart bluetooth, go back to gdm screen and it works.  After I login to gdm, and X starts, the same thing happens again.  After the screensaver starts, same behavior.

I have read a lot of threads on this, but no simple answer.  Everyone says to remove bluez, but I need it for my phone.

Anyone solved this?

Thanks,

Greg

---

### Post by Andrew-buntu on 2007-08-01
I have the same problem with my bluetooth mouse dying after logging in.  But instead of restarting bluetooth, I open the app launcher (alt+F2) or a terminal and type:
```
hidd --search
```
and that makes my mouse and all the other bluetooth devices behave again without having to restart gdm.

---

