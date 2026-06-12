---
title: "Isn't it possible to find an internal modem that works on Intrepid Ibex?"
date: 2009-01-16
forum: Hardware
---

### Post by jkounis on 2009-01-16
I've been trying to get a modem working on Ubuntu 8.10 for a couple of weeks to no avail. Modems are cheap -- I don't mind buying a new modem -- but I'd prefer an internal PCI modem, so I don't add to the cables, power adapters, and external boxes already cluttering up the work area.

So far, I've purchased 3 modems. None of them work with Ubuntu. All of them have turned out to have Conexant chipsets, which seem most common. When I use the Conexant tool to install the driver on my x86_64 system, it says:

> The generic package is not compatible with this system since kernel modules can't be compiled. There is also no pre-compiled package available for your kernel. Please read "Pre-compiled vs. generic packages" for more information.

This error message isn't terribly useful. I already have the linux-source and linux-header packages loaded.

If I try to download the source and build the packages myself, I get the following error:
>   CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c:182: error: field 'semaphore' has incomplete type
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockCreate':
/usr/lib/hsfmodem/modules/osservices.c:194: error: implicit declaration of function 'sema_init'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockLock':
/usr/lib/hsfmodem/modules/osservices.c:221: error: implicit declaration of function 'down_trylock'
/usr/lib/hsfmodem/modules/osservices.c:230: error: implicit declaration of function 'down'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockUnlock':
/usr/lib/hsfmodem/modules/osservices.c:252: error: implicit declaration of function 'up'
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsThreadStop':
/usr/lib/hsfmodem/modules/osservices.c:626: error: implicit declaration of function 'kill_proc'
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsInit':
/usr/lib/hsfmodem/modules/osservices.c:1279: warning: format '%d' expects type 'int', but argument 2 has type 'long unsigned int'
/usr/lib/hsfmodem/modules/osservices.c:1279: warning: format '%d' expects type 'int', but argument 3 has type 'long unsigned int'
make[2]: *** [/usr/lib/hsfmodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2


However, I really would rather not mess with building kernel modules. It's just not worth it to deal with the hassle each time Ubuntu gets a new kernel module. 

My preference is to throw money at the problem and make it go away.

Is there a PCI modem I can just buy that works with Ubuntu x86_64 architecture?

I tried finding a "Controller-Based" modem, but so far, I've struck out. The last modem I purchased, a Diamond SM56PCIWB claims to be "controller-based" according to its documentation, but it still requires the Conexant HSF drivers, which won't compile on my system.

Thanks!

---

### Post by electrogeist on 2009-01-16
Find a used US Robotics Sportster.  IIRC they made some winmodems at the end but I *think* all the Sportsters were real HW modems.   I used to use an external Sportster and my linux box usually connected to my ISP at 54.6 (limit was supposed to be 53)

Personally I'd look for a external Courier, which were the best and big bucks back in the day, I've seen them dirt cheap more recently.

---

### Post by ModelM on 2009-01-16
The [_US Robotics 5610_](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104007) works perfectly - no drivers to install or anything else to mess with. It's a true hardware modem.

---

### Post by electrogeist on 2009-01-16
Oh I didn't realize USR still existed!

---

### Post by jkounis on 2009-01-16
Thank you!

I just put my order in for the U.S. Robotics modem you recommend. The $70 or so that the modem costs is certainly worth it!

---

