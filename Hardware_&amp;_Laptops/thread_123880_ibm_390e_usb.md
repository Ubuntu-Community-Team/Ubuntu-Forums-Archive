---
title: "ibm 390e usb"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by mismis on 2006-01-31
i have installed ubuntu but it does not support my usb port. i have tried reinstalling it serviral times and i noticed that when it is loading the kernel from the cd, usb.rc failed. any help?

---

### Post by FarEast on 2006-02-03
Hi,
Paste the output of the commands below:
$ dmesg | grep usb
$ lsmod | grep usb

What kind of device do you want to use?

---

