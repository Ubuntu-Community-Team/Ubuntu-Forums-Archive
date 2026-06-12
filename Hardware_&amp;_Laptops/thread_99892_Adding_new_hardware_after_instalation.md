---
title: "Adding new hardware after instalation"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by rajko on 2005-12-06
I added new ethernet card in my computer.
What steps should I do to make it work?
I searched around and only thing I found was:
dpkg-reconfigure etherconf.

---

### Post by aysiu on 2005-12-07
System > Administration > Networking?
DHCP seems to work for me. No good for you?

---

### Post by az on 2005-12-07
[QUOTE=rajko]
dpkg-reconfigure etherconf.[/QUOTE]

Etherconf is very useful if you do not have a GUI.  Since the installer does the same thing as etherconf and then you have the GUI, it is not installed by default.

However, if you do not have the default desktop installed, you can install etherconf and it will config your ether from the command line. Is this your case?

The reconfigure command will re-run the setup portion of the package installation which, in etherconf's case is to detect and config your network hardware.

---

