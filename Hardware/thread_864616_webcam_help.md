---
title: "webcam help"
date: 2008-07-19
forum: Hardware
---

### Post by nzadLithium on 2008-07-19
Hey

I've had a e-video dc-350 webcam for a while. I decided to try get it going on ubuntu today. lsusb tells me this about it:
Bus 001 Device 005: ID 0957:0200 Agilent Technologies, Inc. 

I have only one /dev/video* device and that is my tv card so i'm assuming ubuntu has failed to load a module for the webcam.  

Which module do i need to load in order to make this webcam go?

---

### Post by Bitchopper on 2008-07-19
Unfortunately, it is possible that there is no support for your webcam.  The manufacturers typically do not provide any drivers for linux.  You may want to check [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html).  It is the website of a French guy who has written drivers for over 250 webcams.  Maybe there he has written something compatible with what you have.

Hope this helps some.

---

### Post by nzadLithium on 2008-07-20
ok.

Thx for the reply. I'll take a look

---

