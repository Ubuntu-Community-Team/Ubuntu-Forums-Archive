---
title: "How to reset VGA to MESA?"
date: 2009-02-01
forum: Hardware
---

### Post by otara on 2009-02-01
I using ATI 4850 and ubuntu 8.10

I install ATI catalyst and i uninstall coz off the unstable.

but i can't reset the display to mesa.

i have key : sudo dpkg-reconfigure xserver-xorg

but the configure fail,

and i get the info when i glxinfo

aasn@ubuntu:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

and i sure my fglrx oledi uninstall coz when i key
fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found

---

