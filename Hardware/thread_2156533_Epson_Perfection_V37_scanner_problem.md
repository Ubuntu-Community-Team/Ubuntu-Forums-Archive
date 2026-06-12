---
title: "Epson Perfection V37 scanner problem"
date: 2013-06-22
forum: Hardware
---

### Post by Z.K. on 2013-06-22
I have a 386 server with Ubuntu Server 12.04 and I am trying to setup a Epson Perfection V37 scanner.  I managed to get the scanner working with scanimage and created a pdf from the scan which looks quite good actually.  But if I do a scanimage -L I get: > device `epkowa:interpreter:001:005' is a Epson (unknown model) flatbed scanner

Now I have another machine which I use with this scanner and it works correctly as in > device `epkowa:interpreter:001:008' is a Epson Perfection V37 flatbed scanner

It almost seems like the server is not using the epson driver which I installed exactly like I did not my regular desktop machine.  I was wondering if anyone knows how to fix this.  It is not a particular big deal since the scanner does work okay, but it would be nice to have both machines working the same.

:confused:

---

### Post by Z.K. on 2013-06-24
> **Z.K. said:**
> I have a 386 server with Ubuntu Server 12.04 and I am trying to setup a Epson Perfection V37 scanner.  I managed to get the scanner working with scanimage and created a pdf from the scan which looks quite good actually.  But if I do a scanimage -L I get: 

Now I have another machine which I use with this scanner and it works correctly as in 

It almost seems like the server is not using the epson driver which I installed exactly like I did not my regular desktop machine.  I was wondering if anyone knows how to fix this.  It is not a particular big deal since the scanner does work okay, but it would be nice to have both machines working the same.

:confused:

Okay, well I got it working finally.  I noticed that the saned user was not in the saned group.  After adding it, everything works now and I can scan from my other machine.


:D

---

