---
title: "Smart Card Reader for Lucid"
date: 2010-07-27
forum: Hardware
---

### Post by LinuxWhat on 2010-07-27
I have a Smart Card Reader (SCR3310) that I can't get to work on 10.04.  I don't suppose there's a lot of demand for Smart Cards on Linux so it wasn't written into the kernel.  Any thoughts?

---

### Post by ghostborg on 2010-07-27
[http://packages.ubuntu.com/lucid/libccid]("http://packages.ubuntu.com/lucid/libccid")


Looks like you need to add the library package Libccid using Synaptic Package Manager.

This library provides a PC/SC IFD handler implementation for the USB smart
card drivers compliant to the CCID protocol.

In the package description it indicates that the  - SCM Micro SCR 3310 is supported.

Hope that solves your issue.

---

### Post by LinuxWhat on 2010-07-27
Thanks a lot!

---

