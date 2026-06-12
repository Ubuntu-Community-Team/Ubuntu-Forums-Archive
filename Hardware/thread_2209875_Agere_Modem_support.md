---
title: "Agere Modem support"
date: 2014-03-07
forum: Hardware
---

### Post by Titibandit on 2014-03-07
Hello all !

It would be great if I could get my internet modem to work. 
It's an Agere 11c11040 model, that needs the agrsm modules to work.
I found that using the ScanModem scripts and everything.

After some research on LinModems, here is the most relevant page I found : 
[http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)

and the corresponding How to : 
[http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html)

And everywhere on the internet, it's said that I need to compile the driver to get it working.

All of this seems pretty outdated to me and I couldn't get any sources to compile.

So here is my question : Is there a way to get this modem to work ? Or am I trying too hard to do something that is impossible ?

(I am currently using ubuntu 14.04 64bits)

Thanks a lot for your help !

Cheers,
Thibaut.

---

### Post by phidia on 2014-03-08
Hi, I remember getting dial modems to work and specifically the Agere now Lucent models.
I think the ubuntu specific [guide here]("https://help.ubuntu.com/community/DialupModemHowto/Lucent/Agere") is more complete and could work for you. Good luck.

---

### Post by Titibandit on 2014-03-08
Hey,

I picked up the most recent package that is available on their website which is : agrsm-11c11040_20110811_i386.deb
It tries to build the modules using dkms.
I'm trying to build them manually because the automatic build in the package installation failed (because of some dependencies)

so DKMS fails building it and here is the .log of that :
 ```
DKMS make.log for agrsm-11c11040-2.1.80 for kernel 3.13.0-16-generic (x86_64)
samedi 8 mars 2014, 12:00:22 (UTC+0100)
make: Entering directory `/usr/src/linux-headers-3.13.0-16-generic'
  LD      /var/lib/dkms/agrsm-11c11040/2.1.80/build/built-in.o
  CC [M]  /var/lib/dkms/agrsm-11c11040/2.1.80/build/agrsoftmodem.o
/var/lib/dkms/agrsm-11c11040/2.1.80/build/agrsoftmodem.c: In function ‘modem_init_module’:
/var/lib/dkms/agrsm-11c11040/2.1.80/build/agrsoftmodem.c:193:4: error: too few arguments to function ‘add_taint’
    add_taint(TAINT_PROPRIETARY_MODULE);
    ^
In file included from include/linux/cache.h:4:0,
                 from include/linux/time.h:4,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /var/lib/dkms/agrsm-11c11040/2.1.80/build/agrsoftmodem.c:24:
include/linux/kernel.h:402:13: note: declared here
 extern void add_taint(unsigned flag, enum lockdep_ok);
             ^
make[1]: *** [/var/lib/dkms/agrsm-11c11040/2.1.80/build/agrsoftmodem.o] Error 1
make: *** [_module_/var/lib/dkms/agrsm-11c11040/2.1.80/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.13.0-16-generic'
```

what's going on ? in the code bad ?

---

### Post by Titibandit on 2014-03-08
After tikering a little bit more, it seems that this driver was built for linux kernels 2.6 (makes sense because it's quite old) so it gives various errors when trying to build it on a kernel 3.** 
I guess it's a dead end, the author has to update its driver :( ...

---

### Post by Yellow Pasque on 2014-03-08
> **Titibandit said:**
> I guess it's a dead end, the author has to update its driver :( ...

Yes, that's about right. I do know how to workaround the first error...
Change:
```
add_taint(TAINT_PROPRIETARY_MODULE);
```
to
```
add_taint(TAINT_PROPRIETARY_MODULE, LOCKDEP_NOW_UNRELIABLE);
```

So that will get you farther in the build process, but it will only get you more errors (which I don't know how to solve off the top of my head).

---

### Post by Titibandit on 2014-03-08
Yeap, I already get past this error by using : 
add_taint(TAINT_PROPRIETARY_MODULE, false); instead :D
But I run into more errors. I think that debugging them one by one is actually porting the driver to linux kernels 3.** 
Unfortunatly, I don't have the time and knowledge to do such a thing.

---

