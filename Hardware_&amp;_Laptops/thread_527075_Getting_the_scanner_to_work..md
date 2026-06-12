---
title: "Getting the scanner to work."
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by insane_alien on 2007-08-16
Hey, i'm trying to get my PrimaScan Colorado 2400u scanner to work but i'm not getting very far.

when i try to preview with xsane i get the generic image on it which is no help and when i try to scan it crashes. using the terminal i get the error output 
```
Floating point exception (core dumped)
```

also, here is the relevant part of lshw

```
 *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: USB Scanner
                   vendor: Primax
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-1.00
                   configuration: maxpower=48mA speed=12.0MB/s

```

if you need anything else then i will be happy to post it. i haven't been able to find a linux driver for it so i'm not sure if one exists.

---

### Post by linuxwizard on 2007-08-16
From what I see that scanner is not supported. It is not listed and most of Primax scanner looks like are not supported. It is not going to work under linux.

[http://www.sane-project.org/sane-mfgs.html#Z-PRIMAX](http://www.sane-project.org/sane-mfgs.html#Z-PRIMAX)

---

### Post by insane_alien on 2007-08-16
oh. damn it.

---

### Post by Pinoy915 on 2008-04-04
Do any of you still have this scanner? I tried to get the drivers to work but I was getting errors. I am not on my machine at the moment to output the errors but if you want to try to use these drivers to get the Primascan 2400u to work under Linux, here is the website:

[http://www.geocities.com/trsh0101/index.html]("http://www.geocities.com/trsh0101/index.html")

---

### Post by oldsoundguy on 2008-04-04
Just remember that any piece of computer equipment you buy for $19.99 at a drug store or super market will be rather suspect for getting drivers in Linux.

---

### Post by Pinoy915 on 2008-04-05
I had this scanner even before I ventured into the Linux world. This scanner is very old, lol.

---

### Post by Pinoy915 on 2008-04-29
I got the scanner working. It will work with basic functions but it is enough for me to copy documents. Just install build-essential, libusb, libusb-dev and the program should compile.

---

