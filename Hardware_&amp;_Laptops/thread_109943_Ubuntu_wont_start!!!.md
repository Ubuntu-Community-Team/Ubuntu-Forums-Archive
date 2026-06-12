---
title: "Ubuntu wont start!!!"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by ghosthead123 on 2005-12-29
Question Problems with Ubuntu 5.10 & 5.04 live & install CD.
I have an GIGABYTE W511 notebook.
When I try to boot with the default live or install system it starts booting and after a few seconds I get the message: 'Uncompressing Linux...ok, booting the kernel' and then nothing at all happens.
I have no idea what to do, can you help me?

PS: I'm sorry if my english is not very good

Thanks!:confused: :confused: :confused:

---

### Post by Luzbel on 2005-12-29
Try the following boot parameters (I'll try them in this order):

pci=noacpi

acpi=off

noapic

nolapic

If none works, try combining them ;)

---

