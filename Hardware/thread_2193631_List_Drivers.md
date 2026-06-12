---
title: "List Drivers"
date: 2013-12-13
forum: Hardware
---

### Post by borgward on 2013-12-13
Hi 

what command line do I use to determine which drivers are installed and what hardware they are associated with.

---

### Post by Bashing-om on 2013-12-13
borgward; Hi !

A lot depends on what you are looking for:

lspci -> List all PCI buses and devices connected to them. This generally includes network cards and sound cards.
lsusb -> List all USB buses and any connected USB devices, such as printers and thumb drives.
lshal (depreciated in 13.10 (??) -> List all devices the hardware abstraction layer knows about , all the hardware on the system.
lshw -> List the hardware on the system including the maker, type, and where it is connected.

I bet there are more .. and when ya want to get specific I know of many more - this will give ya a good place to start.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by borgward on 2013-12-14
Broadcom Wireless mini card

---

### Post by steeldriver on 2013-12-14
in that case I'd try something like

```
sudo lshw -C network -sanitize
```

or

```
$ lspci -vnn | grep -A10 '\[02.0\]'
```

to find the network adapter(s) in the PCI hierarchy and print the 10 following lines

---

