---
title: "Epson stylus photo rx620"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by ildfroe on 2005-10-31
Has anyone managed to make this printer/scanner work?
Using breezy's built-in printerdriver (epson stylus rx600), I can print just fine. However I can't use the scanner. I have downloaded the iscan rpm from epson's avasys site. But when I start iscan I get a message box: "Could not send command to the scanner."
Any ideas??

---

### Post by ildfroe on 2005-11-01
Anyone?

---

### Post by El lolo on 2006-01-29
Hello

I've just got the same printer.

Your scanner should run with a root account.
If so, add this in /etc/hotplug/libsane.usermap :

# Epson Corp.|Stylus RX620
libusbscanner             0x0003      0x04b8   0x0811    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x00000000

You should be able to run xsane with a normal user account after a reboot.

Did you manage to print photos ?

---

