---
title: "Looking for scanner help"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by DaBigUA on 2006-07-12
Hello.  I am trying to figure out how to make my Epson scanner (Perfection 4180) work under Kubuntu/KDE 3.5.2.  SANE databases lists its support as "good." I'm sure I have some of the pieces, I just don't know how they fit together.

In KDE, Xsane, Kooka and GIMP all cannot see a scanner.

From the shell, **sane-find-scanner** finds the scanner, and reports:

```
found USB scanner (vendor=0x04b8, product=0x0118) at libusb:006:006
```

But **scanimage -L** reports:

```
No scanners were identified.
```

I presume I must install and/or modify configuration files?  I downloaded the epkowa backend referred by the SANE website, but that appeared to be binaries.  Some posts talk about /dev/usb (which doesn't exist on my system) and others talk about /etc/sane.d (which has both epson and epkowa configuration files).

Clearly I don't know what I am doing.  I am very frustrated.  I am ready to quit dual-booting and go to Linux full time.  But if I can't scan, it won't work, so I am very eager to piece this together.

Any help is greatly appreciated.  Cut-and-paste fixes are great, but what I most desire is to understand what is broken and how it can work.  

Thanks in advance.

- Andrew

---

