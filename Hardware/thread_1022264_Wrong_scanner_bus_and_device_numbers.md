---
title: "Wrong scanner bus and device numbers?"
date: 2008-12-26
forum: Hardware
---

### Post by Charlotte18 on 2008-12-26
When I try to start XSane, I get the following message:
```
Failed to open device 'brother2:bus5;dev1'
Error during device I/O
```
It seems to me that the app is looking at the wrong bus and dev. When I go to terminal and type "lsusb," I see the Brother device at Bus 001, Device 002. This is a Brother DCP 7020 Copier-Scanner-Printer. Always worked under Hardy, but now I'm in 8.10.

Anybody know what going on here and how to fix it?

---

### Post by Charlotte18 on 2008-12-26
In reality, the problem is that the scanner only works when run as root. Anybody know how to fix this so that my normal user account has permission? When I go to System > Administration > Users and Groups, my account has permission to "Administer the system" and to "Use scanners." 

But still scanning only works when run as root.

Anybody know how to fix this in 8.10?

EDIT: I've run the following commands in terminal. Still no luck.
```
sudo chmod ugo+rwx /dev/bus/usb/
sudo chmod ugo+rwx /dev/bus/usb/*
```

Anybody?

---

