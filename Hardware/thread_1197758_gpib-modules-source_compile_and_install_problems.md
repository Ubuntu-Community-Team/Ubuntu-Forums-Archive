---
title: "gpib-modules-source compile and install problems"
date: 2009-06-26
forum: Hardware
---

### Post by skintythe1andonly on 2009-06-26
Hi

I am currently trying to install the modules in order to get drivers for a NI GPIB-USB-HS, but am a bit unsure of what I am doing. 

National Instruments did provide linux drivers but only up until kernel 2.4

I have installed the gpib-modules-source.... extracted it and tried to compile it just by calling "make" but all I get is

```

make: Nothing to be done for `default'.

```

If I check the documentation it says to check the INSTALL file.... but there is none.

I then decided to download the package directly from sourceforge. This package is a lot more comprehensive. It has a ./configure file, and does compile, and an INSTALL file in which they state I have to recompile the kernel with this. 

I dont really want to do this and thought there was an easier way of doing this on ubuntu from kernel 2.6 onwards. I preferably would want to compile the source files from the gpib-modules-source package in the repos and load this into the current kernel. How do I do this?

---

