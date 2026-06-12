---
title: "fglrx 8.632 problem with DKMS?"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by ENatanael on 2009-08-03
I've now tried so many times and messed up almost as many so I feel like I have to ask.
I'm trying to install the proprietary ATI driver version 8.632 on Ubuntu Jaunty 64 using a custom real time kernel (2.6.29.6-rt23). I have now been able to install it, but at startup it says something like "DKMS auto installation ... fglrx [fail]" and flgrx info and glxinfo both give the same error message:

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

Scrolling webpages and moving windows is choppy. Starting Savage 2 (which is what I've choosen for testing the drivers gives almost the same error as above:

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  23
  Current serial number in output stream:  23


When I try to start my other kernels now (2.6.28-14-generic and 2.6.28-11-generic) all I get is a black screen which locks and I have to manually shutdown the computer.

My graphics card is the ATI Radeon Mobility HD 4570 on a Dell Studio 1555 (laptop).

---

### Post by joezamboni on 2009-09-23
fglrx is no longer relevent

---

### Post by ENatanael on 2009-09-24
For me the problem fixed itself with the newer driver (9.8 aka 8.64). I have not tried the newest one (9.9 aka 8.65).

---

### Post by g-raf on 2009-09-25
I've had the same problem, with the same choppyness and same thing in the terminal when i type "fglrxinfo," i get > X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14


I have a Mobility Radeon HD 3400 Series, using the rt kernel on Ubuntu Studio 9.04.

---

### Post by g-raf on 2009-09-25
> **ENatanael said:**
> For me the problem fixed itself with the newer driver (9.8 aka 8.64). I have not tried the newest one (9.9 aka 8.65).

I just tried installing 9.8 and had the same results.

---

