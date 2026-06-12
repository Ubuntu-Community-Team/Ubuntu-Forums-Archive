---
title: "Need Help..."
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by hotcha3 on 2006-05-11
Hi, , im a linux newbie, i really need some help with an issue:

I bought an AvertTV dvb-t USB 2.0 and i've been trying to make system recognize it for like a week but i can't. I've found a nice guide here: [http://www.wi-bw.tfh-wildau.de/~pboe...=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboe...=dvb-usb-howto)

which has helped me alot, but i have a problem after the cvs checkout when i start to compile: when i press: :~/dvb-kernel/build-2.6$ make

i keep getting : Makefile:13: /lib/modules/2.6.15-22-386/source/.config: FIle or directory doesen't exist
make: *** there's no rule to build the objective `/lib/modules/2.6.15-22-386/source/.config'. Alto.


I really don't know anything about compiling but it's the only way i've found to make my dapper (i tried unluckily with breezy) recognize it. I would really appreciate if someone could help me. Than****

---

### Post by cyracks on 2006-05-11
install **linux-kernel-headers** and **linux-headers-x.x.x** where x.x.x correspond to your kernel image

---

### Post by hotcha3 on 2006-05-11
Thanks for asnwering.

I already had installed linux-headers-2.6.15-22-386 and the kernel-source too, but i still get the same problem, any idea of what should i do now ?

---

### Post by cyracks on 2006-05-11
Realy don't know but maby it would help if you compile your own kernel:
[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)

---

### Post by hotcha3 on 2006-05-11
But i just upgraded to Dapper yesterday, and i installed the headers and source..i'ts really weird, and im really desperate... im starting to miss windows xD

---

### Post by cyracks on 2006-05-11
From this site I would assume that it is supported under linux
[http://www.mediaatlantic.com/product.php/25397/1//811cb2d79b933947e531d7b6538a51d8](http://www.mediaatlantic.com/product.php/25397/1//811cb2d79b933947e531d7b6538a51d8)

Does system recognize it correctly
```

lsusb

```

---

### Post by hotcha3 on 2006-05-11
Yes, it recognizes it: 

Bus 002 Device 002: ID 07ca:a800 AVerMedia Technologies, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0425:0101 Motorola Semiconductors HK, Ltd G-Tech Wireless  Mouse & Keyboard
Bus 001 Device 001: ID 0000:0000

And i've found a guide of a guy that has the same on debian, and it's the guide i followed...the problem is i can't even start to compile the drivers... there's not a source folder...

---

