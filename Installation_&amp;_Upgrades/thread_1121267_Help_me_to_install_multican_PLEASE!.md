---
title: "Help me to install multican PLEASE!"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by I eat coffee! on 2009-04-09
Someone help me install this program. The untared folder does not contain an INSTALL file. Here is a link to where it can be downloaded. Please help me out. This software is used for remote control of the cannon 350d dslr cameras. If you have another way of controlling them via pc, please share. The readme does not tell me how to install. Do I need to download an ide in order to compile it...?

[http://multican.sourceforge.net/](http://multican.sourceforge.net/)

---

### Post by knattlhuber on 2009-04-10
The way to go would be to do
```
sudo make install
```
in a terminal.

Or better, after installing the 'checkinstall' package
```
sudo checkinstall
```
(checkinstall will create a .deb package that can be removed should you wish to remove it later)

However, when I do that on my machine, make throws an error
```
multican.c:32:17: error: usb.h: No such file or directory
```
complaining about a missing header file. You may have to install an additional library but I don't know which one. libusb-dev maybe?!?

---

### Post by I eat coffee! on 2009-04-10
I tried all of that but I got errors. should I find and install that library? I was hoping multican would contain a INSTALL file to educate me on its dependencies. I guess the creator was not interested in making it remotely easy to install haha.

---

### Post by knattlhuber on 2009-04-10
I had googled the error message and people had suggested installing libusb-dev to fix it. Doesn't hurt to try I guess...

---

