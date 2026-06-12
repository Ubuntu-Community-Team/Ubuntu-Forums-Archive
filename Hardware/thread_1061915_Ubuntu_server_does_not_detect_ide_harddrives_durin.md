---
title: "Ubuntu server does not detect ide harddrives during install."
date: 2009-02-06
forum: Hardware
---

### Post by alex1996arm on 2009-02-06
I have the ubuntu server 8.04 installation disks,i boot from them and it wont find my disk drives.it asks me to select a driver out of a hundred and i dont know what one to pick.the machine is fairly old(1998)

---

### Post by az on 2009-02-06
The server kernel is different than the desktop kernel, but you can run a server using the Desktop kernel.  The Desktop kernel handles more hardware but is not tweaked for server performance like the Server kernel.  On older hardware, you wouldn't benefit from those optimisations that much anyway.

It used to be that the installer booted the Desktop kernel and installed the Server kernel when you chose to install a server setup.  If that has changed, you may be booting with the server kernel when you boot the server install disk.

Does the desktop cd boot on this machine?

---

### Post by alex1996arm on 2009-02-06
thank you,i will try and post back.

---

### Post by alex1996arm on 2009-02-06
it does thanks,i found a guide online:):p

---

