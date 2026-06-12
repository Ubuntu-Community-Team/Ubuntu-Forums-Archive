---
title: "Epson Scanner"
date: 2008-05-10
forum: Hardware
---

### Post by mucmicu on 2008-05-10
Hi there

I just find [this tutorial]("http://ubuntuguide.org/wiki/Dapper#How_to_install_a_USB_scanner") about how to install a scanner.

All works fine until i have to 
```
 $ grep Epson /etc/udev/rules.d/45-libsane.rules
```

I don't have 45-libsane.rules file. 
why that? what to do?

---

### Post by pointym5 on 2008-05-10
That's Hardy bug #188552 in sane-backends.

---

### Post by Dai777 on 2008-05-12
look for 025-libsane-extras.rules

---

