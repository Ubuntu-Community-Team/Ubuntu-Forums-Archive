---
title: "boot from USB stick hung"
date: 2009-12-18
forum: Hardware
---

### Post by luboi on 2009-12-18
Hi there, 
  I tried to install Ubuntu 9.10 on usb stick (4 GB PQI) and it worked fine except for ending up without much space after getting all I wanted. So I decided to get something bigger - 16GB Kingston 101 data traveler. After installation, I tried to start the OS, ... and failed. OS hangs after switching to graphical screen. Any hint what did I mess up, and even better what do I do, to fix it?

Thanx in advance

---

### Post by efflandt on 2009-12-18
If you actually installed it to USB (instead of USB Startup Disk Creator with live iso in vfat), what filesystem type did you use, and did you put grub on the USB stick (instead of default to main hard drive)?

What video card do you have (what shows for it in **sudo lspci -v**) and does it normally work with standard modules?

Does it get as far as gui login, or is it failing after that starting gnome (does **FailsafeGNOME** work from dropdown list in gui login)?

---

### Post by luboi on 2009-12-18
OK, reply helped in following way: I started up in recovery mode and ... saw quite lot I/O errors. This might (according to me) mean either problem with the stick (corrupt stick) or problem with file system. I will check the stick, and try using ext3 instead of ext4. Thanx! it kicked me forward :D

---

### Post by luboi on 2009-12-18
:( ... no reasonable result. when trying to boot from the stick, recovery mode boot indicates I/O errors. changing FS does not help. USB stick tested as non boot drive in Win & Linux, works fine - both write and read operation works fine. any hint now?

---

