---
title: "lexmark x73, cant get scanner to work, hardy"
date: 2008-09-07
forum: General Help
---

### Post by burton247 on 2008-09-07
I have a lemark x73 that prints fine but sane give the error message
"failed to open device `gt68xx:libusb:004:003`:
invalid argument"

so i had a look around and followed the following guide
[http://ubuntuforums.org/showthread.php?t=470431](http://ubuntuforums.org/showthread.php?t=470431)
with no success

can someone help me please

---

### Post by burton247 on 2008-09-11
no?

---

### Post by Terence Hood on 2010-05-06
To solve this problem you need to download and install the firmware file the error message is referring to.

Here is a site you can find the firmware for the** X73** and some other printers.
[B][http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)
[/B]
**1) Download File - [http://subfusion.net/drivers/oslo3071b2.usb](http://subfusion.net/drivers/oslo3071b2.usb)**

[B]2) Copy the oslo3071b2.usb firmware file into directory /usr/share/sane/gt68xx
[/B]
Note: some systems may need the file located in /usr/local/share/sane/gt68xx

Having trouble copying the file to the directory? Open a terminal screen and CD (change directory) into the directory you saved the file to and use this command. It will ask for the super user password to override any copy permissions you might be running into.

**sudo cp oslo3071b2.usb /usr/share/sane/gt68xx**

Once the file is in this directory Xsane should work.

Side Note : If you are looking for general printing help / drivers for your Lexmark X73 here are some additional resources to look into.

[SIZE=2]_**Gutenprint**_[/SIZE]
[B]Project Site - [http://gutenprint.sourceforge.net](http://gutenprint.sourceforge.net)
Download Site - [http://sourceforge.net/projects/gimp-print/files/](http://sourceforge.net/projects/gimp-print/files/)
[/B]

---

