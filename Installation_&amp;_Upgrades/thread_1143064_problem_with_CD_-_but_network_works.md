---
title: "problem with CD - but network works"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by ilantal on 2009-04-29
I am trying to install 9.04 but I must have a problem with my CD.
I have my home on partition sda3 and I formatted sda1.
The live cd comes up but when I try to install it can't read some sector on the cd after 26% of the files have already been transferred.
I tried burning a second cd, but that one won't even bring up live cd.
However, I can use my first cd to bring up live cd and then I can look through the LAN to my other computer and see the ubuntu install cd on the second computer.
I am wondering if there is a way to either install through the LAN or maybe copy the contents of the cd onto the home partition and install from there?
If I try to boot directly to my disk, it is dead (because the copying of the files didn't finish).
What is the best way to proceed?
Thanks,
Ilan

---

### Post by CMJ Tech on 2009-04-29
Is the computer you are trying to install 9.04 running windows?  If so, then we may be able to use unetbootin to create a bootable iso on your hard drive.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ilantal on 2009-04-30
No, my laptop is pure Ubuntu. It is connected to a router where I also have a Windows machine. I used the Windows machine to generate the CD and I can see (and read from) that CD via the LAN.

---

### Post by CMJ Tech on 2009-04-30
The following link list different ways to install over network or internet.

[https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations](https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations)

---

