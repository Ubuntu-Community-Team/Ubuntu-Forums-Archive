---
title: "Linux equivalent to Window's Device Manager"
date: 2018-09-15
forum: Hardware
---

### Post by jdeiros on 2018-09-15
Basically, I want to see ALL the devices on my PC, and what kernal drivers are installed.

Is ```
lspci -knn
``` as close to what I am asking for? How do I know it's picking up everything and not just things with drivers installed already?

---

### Post by jeremy31 on 2018-09-15
The lspci command will list all devices connected to the PCI bus whether there are drivers or not, if you are looking for a GUI program try hardinfo

---

### Post by yancek on 2018-09-15
You should get more information with the command:  inxi -F

---

### Post by Yellow Pasque on 2018-09-17
There's lshw-gtk as a GUI, though its interface is a bit awkward IMO.

> How do I know it's picking up everything and not just things with drivers installed already? 

If the device is on the PCI bus, lspci will list it regardless of whether a kernel module is loaded for it or not.

---

