---
title: "Easy USB Scanner Permission Fix"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by sharke on 2007-04-03
If Like me you can only run Xsane as root the fix is.

Sudo gedit /etc/udev/rules.d/40-permissions.rules and changw the usb subsystem to mode 0666 reboot and xsane should find scanner as user.
Regards
Sharke

---

### Post by guitarchris on 2007-07-15
> **sharke said:**
> If Like me you can only run Xsane as root the fix is.

Sudo gedit /etc/udev/rules.d/40-permissions.rules and changw the usb subsystem to mode 0666 reboot and xsane should find scanner as user.
Regards
Sharke

Hi. I tried this to get my Epson 3850 scanner to work with xsane but my permissions were already like this. xsane still reports "no device found".
The printer side (it's a multifunction) works fine.
Any help gratefully received,
Guitarchris

---

