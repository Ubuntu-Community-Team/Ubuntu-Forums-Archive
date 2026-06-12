---
title: "Need help with PCI Dual Parallel Port Card"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by JustPlaneSweet on 2006-10-20
I am trying to get a Rosewill RC-304 PCI dual parallel port card to function under Dapper.  The computer is a Dell Dimension L1000R desktop.

The board is identified by lspci as a Communication controller: NetMos Technology PCI 9815 Multi-I/O Controller (rev 01) with a Vendor id 9710 and Device id 9815

lspci -v shows:

0000:01:09.0 Communication controller: NetMos Technology PCI 9815 Multi-I/O Cont roller (rev 01)
        Subsystem: LSI Logic / Symbios Logic 2P0S (2 port parallel adaptor)
        Flags: medium devsel, IRQ 9
        I/O ports at dff0 [size=8]
        I/O ports at dfe0 [size=8]
        I/O ports at dfa8 [size=8]
        I/O ports at dfa0 [size=8]
        I/O ports at df98 [size=8]
        I/O ports at df80 [size=16]

How do I tell parport (or parport_pc) to use the parallel ports?

Thanks,

Stan

---

