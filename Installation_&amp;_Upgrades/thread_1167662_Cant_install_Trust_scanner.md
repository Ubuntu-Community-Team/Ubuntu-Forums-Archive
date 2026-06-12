---
title: "Cant install Trust scanner"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by alan mckeeve on 2009-05-23
I am trying to install a scanner, Trust 24TH Direct Webscan Gold, so far when I open xsane this is what I get, Failed to open device 'gt68xx:Libusb:004:002': invalid argument  I have browsed around and found I need to change something to this "A2fw.usb" but I do not know where or how. The version of Ubuntu I am using is 8.10. This is the first time I have had to ask for help, I usually manage with information I find here. thanks to anyone who can help.

---

### Post by Agent Smith on 2009-06-10
You need to add the file "A2fw.usb" to the "usr/share/sane/gtkxx" folder. If you dont have the file heres a link.

[http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/A2fw.usb](http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/A2fw.usb)

Hope this helps Jon.

P.S You will have to be root to add it!

---

### Post by Agent Smith on 2009-06-10
Oh by the way, you will have to create the folder if it does not exist.

---

