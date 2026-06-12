---
title: "smart link modem usb"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by enrico7961 on 2005-10-17
Hello

I’m enrico from Italy, I’m a beginner with Linux so I’m looking for someone who can help me.

I’ m having some problems installing an Usb modem, I read everything I found in the forum and also in the internet, I was able to fix a lot of the previous problems but now I’m stuck with this problem .

I’m installing Smart Link soft modem on Ubuntu with 2.6.12-6-386 kernel, but when I use make I get these errors:

eric61@ casa:-/Desktop$ cd slmodem-2.9.10 make clean
eric61@ casa:-/Desktop/slmodem-2.9.10$ make
make –C modem all
make[1]: Entering directory ’/home/eric61/Desktop/ slmodem-2.9.10$ modem’
gcc –Wall –g -0 –I. –DCONFIG_DEBUG_MODEM  –o modem.o  - c modem.c
modem.c: In function  ‘modem_reset’:
modem.c: 1701: error: invalid storage class for function ‘sregs_init’
modem.c: 1713: warning: implicit declaration of function ‘sregs_init’
modem.c: At top level:
modem.c: 1727: error: static declaration  of ‘sregs_init’ follows non-static declaration
modem.c: 1713: error: previous implicit declaration of ‘sregs_init’ was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory ’/home/eric61/Desktop/ slmodem-2.9.10/modem’
make[1]: *** [modem] Error 2
	
Is there anyone who can help me?

Thanks

enrico

---

### Post by elfgoh on 2005-10-19
Keep an eye here:

[http://www.ubuntuforums.org/showthread.php?t=77537&page=2&highlight=gcc](http://www.ubuntuforums.org/showthread.php?t=77537&page=2&highlight=gcc)

---

