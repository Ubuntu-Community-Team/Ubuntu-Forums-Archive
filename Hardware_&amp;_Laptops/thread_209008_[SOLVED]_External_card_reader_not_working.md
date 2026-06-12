---
title: "[SOLVED] External card reader not working"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by SPW06 on 2006-07-04
Hello,

I have a generic USB 2.0 card reader made by promaster that wont work.

I'd love to be able to get my pictures off my camera and on to my desktop :D

Any ideas?

---

### Post by Volfied on 2006-10-01
I'm suffering from the same thing, can someone please answer this?

-Up!

---

### Post by jISh on 2006-10-01
What happens when you plug it in? Can you post the output of the following command directly after you plug it in?
```
dmesg |tail 
```

---

### Post by Volfied on 2006-10-01
[17245189.856000] usb 1-1: device descriptor read/64, error -32
[17245190.072000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[17245190.204000] usb 1-1: device descriptor read/64, error -71
[17245190.440000] usb 1-1: device descriptor read/64, error -84
[17245190.656000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[17245190.672000] usb 1-1: device descriptor read/8, error -75
[17245190.792000] usb 1-1: device descriptor read/8, error -71
[17245191.008000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[17245191.232000] usb 1-1: device descriptor read/8, error -32
[17245191.356000] usb 1-1: device descriptor read/8, error -32

---

### Post by SPW06 on 2007-08-02
An upgrade to Ubuntu 7.04 Feisty Fawn solved this :)

---

