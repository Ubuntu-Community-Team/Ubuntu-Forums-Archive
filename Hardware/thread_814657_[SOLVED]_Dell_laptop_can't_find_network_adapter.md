---
title: "[SOLVED] Dell laptop can't find network adapter"
date: 2008-05-31
forum: Hardware
---

### Post by ScottyP on 2008-05-31
So I just installed Hardy on my Dell Inspiron 8100 laptop. Everything is cool and fine until I try to connect to my network. As it turns out, my laptop has no clue it even has a NIC.

The card that's in there is: 3Com 3CCFE575CT 10/100 MB Ethernet Cardbus PC Card

Unfortunately, running "ifconfig -a" only shows my loopback info.
Running "lspci" doesn't even list an ethernet adapter.

How do I convince this bird that there really is a network card?

Thanks!

---

### Post by Ayuthia on 2008-06-01
Does the device show up under lsusb?

---

### Post by ScottyP on 2008-06-01
So I fixed my problem. It had absolutely nothing to do with Hardy. The same problem would've happened regardless of the operating system because....

...I opened up my laptop to see that my Mini PCI card was halfway unplugged. DOH!

[How to check Mini PCI card on Dell Inspiron 8100]("http://support.dell.com/support/edocs/systems/ins8100/en/sm_en/remove.htm#1050760")

Thanks for the help anyways

---

