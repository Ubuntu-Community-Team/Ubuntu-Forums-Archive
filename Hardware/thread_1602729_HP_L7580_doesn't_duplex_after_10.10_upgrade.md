---
title: "HP L7580 doesn't duplex after 10.10 upgrade"
date: 2010-10-21
forum: Hardware
---

### Post by lucasl on 2010-10-21
Hi,
I have an HP Officejet Pro L7580 connected to my network. It used to work fine, duplex included, however after upgrading to 10.10, there is only a "One-sided" option in the two-sided dropdown in the printing dialogue. I tried deleting and re-adding the printer, and also checking the "Duplexer Installed" option in the printer settings (which I hadn't seen previously) but to no effect.

Thanks!

---

### Post by lucasl on 2010-10-25
Also, the build seems pretty hackish... hp-check reveals a bunch of compile time options enabled that don't apply to a standard Ubuntu install as well as a bunch of dependencies it thinks are missing including:
```

Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

...and so on for libjpeg, libcrypto, libnetsnmp-devel, libusb, pyqt4 dbus, python devel and SANE devel...

# Following values are determined at configure time and cannot be changed.
[configure]
scanner-build=yes
fax-build=yes
dbus-build=yes
ui-toolkit=qt4
qt4=yes
```

I assume the Qt4 stuff is so the package manager has an easy time but might it cause problems? But I guess it was probably this way before duplex stopped working...

---

### Post by lucasl on 2010-10-25
[https://answers.launchpad.net/hplip/+question/130814](https://answers.launchpad.net/hplip/+question/130814)

In the end a manual install to the latest version fixed it... But it's awfully messy and now I have Qt installed... gross.

---

### Post by bertmung on 2010-10-25
I'm having the same problem with duplex printing.

I installed HPLIP 3.10.9 and still have no duplex.

At [https://answers.launchpad.net/hplip/+faq/1356](https://answers.launchpad.net/hplip/+faq/1356) I'm advised to

open installer/distroes.dat file in the hplip-3.10.9 directory and apply the following diff patch content on the file.
from hplip-3.10.9 directory launch ./install.py file to continue auto installation.


The part I'm particularly confused about is "apply the following diff patch content ..."

---

### Post by lucasl on 2010-10-25
At that link, copy from near the top "Index: installer/distros.dat" to "index=2" and paste it into a blank file named patch.diff

Then you just open a terminal, cd to the right directory and type in
```
patch installer/distroes.dat patch.diff
```

---

### Post by lucasl on 2010-10-25
Hold up, looks like I prematurely thought this was fixed. Even though the printer appears to be able to do duplex in the printer settings utility, in the print dialogue it's still one sided...

---

