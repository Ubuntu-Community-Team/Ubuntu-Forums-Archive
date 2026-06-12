---
title: "GtkTerm not working for PCI serial card"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by craftybones on 2007-01-08
Hello,

I have a system which has a NetMOS serial multiport pci card. Ubuntu seems to detect it fine and loads the module as well. lspci lists it etc. Under dmesg these serial ports show up as ttyS4-ttyS7.

However, when I load up gtkterm, only /dev/ttyS[0-3] are found. I read some wonderful documentation on the subject, however its unclear to me as to what the problem is.

[http://www.tldp.org/HOWTO/html_single/Serial-HOWTO/]("http://www.tldp.org/HOWTO/html_single/Serial-HOWTO/")

Can someone tell me if they've faced this problem?

In a related problem, minicom does the same thing, where it refuses to connect to this device. The strange bit with minicom however is that it used to connect to these ports before I installed gtkterm.

can anyone help me solve this mystery?

Jayanth

---

