---
title: "Using a custom name for a printer..."
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2005-09-07
So this is a story... I have already repeated it somewhere, but would like to put it all together.

I have to computers. One is my laptop which is a pure Ubuntu box, another is a desktop, which is dual boot. The printer is connected to the desktop and both coputers are in wireless network. 

I would like to print to the printer from my laptop whenever it is booted into Windows or Ubuntu. So the advice I've got is to set up two queues/printers in CUPS:  one for Windows SMB printer and another for Linux CUPS printer on the laptop, then to put those queue/printers into one class and set this class as a default printer. Theoretically it should work. 

However, as it is phisically the same printer it is called Stylus-Photo-790 in SMB and CUPS, meaning that I cannot put two printers with identical names into one class. 

I tried to change the name of those printers without any luck. Ok, I tried to reinstall my SMB printer under different name. But the problem is that if I use gnome-cups-manager (Administration-Printing), it uses default name mentioned above. I tried to use web interface which I enabled (localhost:631). It allows me to name the printer differently, but I cannot put my login name and password there. It is also impossible to change password and login name using gnone-cups-manager.

Basically I need either rename a printer, created with GUI app or add user name and password to the printer created using CUPS web interface. Does anyone know how it is possible to accomplish?

---

