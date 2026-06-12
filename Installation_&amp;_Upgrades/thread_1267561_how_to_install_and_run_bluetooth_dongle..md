---
title: "how to install and run bluetooth dongle."
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by charlie090790 on 2009-09-15
hi, i recently purchased a new bluetooth dongle for my acer aspire netbook and need help getting it to run on Ubuntu 9.04. thnx :)

---

### Post by inobe on 2009-09-15
lets start with the brand model of usb bluetooth device ?

i recently bought a d-link for 20$ at radio shack, it works great using blues.

---

### Post by charlie090790 on 2009-09-15
im not sure whats the mode(bought it on ebay lol). but i get this when i type lsusb in terminal: 
>Bus 002 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

---

### Post by inobe on 2009-09-15
what do you get when you go to system> preferences> bluetooth


is the device not found ?

---

### Post by charlie090790 on 2009-09-15
it find it sometimes and then doesnt at other times.

---

### Post by inobe on 2009-09-15
when it doesn't find the device open terminal

```
lspci
```

see if the device is still listed

---

