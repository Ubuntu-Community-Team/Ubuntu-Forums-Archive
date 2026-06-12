---
title: "slmodem on Toshiba Satellite A35"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by HairyDave on 2006-03-22
Hi,

I wonder if someone could assist me with this problem:

I am trying to add slmodem so that I can use the 'soft'modem on my laptop. However when I try to 'make' slmodem I get the following:

[COLOR="Blue"]$make
make -C modem all
make[1]: Entering directory `/home/Utilities/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -o modem.o -c modem.c
modem.c: In function "modem_reset":
modem.c:1701: error: invalid storage class for function "sregs_init"
modem.c:1713: warning: implicit declaration of function "sregs_init"
modem.c: At top level:
modem.c:1727: error: static declaration of "sregs_init" follows non-static declaration
modem.c:1713: error: previous implicit declaration of "sregs_init" was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/Utilities/slmodem-2.9.10/modem'
make: *** [modem] Error 2
$[/COLOR]
](*,) 

What am I doing wrong with this or is there some other way I get the modem to work??

I have run scanModem and it recognises the modem and chipset.
__________________________________________________ _________

"For the things we have to learn before we do them, we learn by doing them."
Aristotle

---

### Post by fizgig on 2006-03-23
Take a look at my site: [http://mattsmith.hostmatrix.org/zx5078cl/](http://mattsmith.hostmatrix.org/zx5078cl/)

I got slmodem working on my laptop.

---

### Post by HairyDave on 2006-03-23
Thanks for the info Fizgig, I will try this out tonight when I get home.  
Hopefully I can get my head round this as I am still on the New Linux user cloud.

---

### Post by towsonu2003 on 2006-04-14
is this resolved?

---

