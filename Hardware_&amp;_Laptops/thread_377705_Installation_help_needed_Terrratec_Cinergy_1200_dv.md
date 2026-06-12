---
title: "Installation help needed: Terrratec Cinergy 1200 dvb-c"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by j4ni on 2007-03-06
I bought Terratec Cinergy 1200 dvb-c cause I had read it has a good linux support and it works out-of-the-box . Unfortunately there is a newer version of Cinergy 1200 dvb-c which doesn't work out-of-the-box. 

There is an experimental driver but I can't get it work.
I have tried to follow this howto: 
[http://www.cs.helsinki.fi/u/aulaskar/digi/terratec_cinergy_1200_dvb-c.html](http://www.cs.helsinki.fi/u/aulaskar/digi/terratec_cinergy_1200_dvb-c.html)

(1)
The first problem that I face: 
> apt-get install kernel-headers-`uname -r` build-essential
> Reading package lists... Done
> Building dependency tree... Done
> E: Couldn't find package kernel-headers-2.6.15-28-386

Are kernel-headers same as linux-headers?
If not where can I get kernel-headers?


(2)
If I continue (using linux-headers):

Next error pops up when building modules

> make
(Here are just the last lines. If needed, I'll paste them all.)
...
  CC [M]  /usr/src/v4l-dvb/v4l/dvb-usb-i2c.o
  CC [M]  /usr/src/v4l-dvb/v4l/dvb-usb-dvb.o
  CC [M]  /usr/src/v4l-dvb/v4l/dvb-usb-remote.o
  CC [M]  /usr/src/v4l-dvb/v4l/usb-urb.o
  CC [M]  /usr/src/v4l-dvb/v4l/em28xx-video.o
/usr/src/v4l-dvb/v4l/em28xx-video.c: In function 'em28xx_init_dev':
/usr/src/v4l-dvb/v4l/em28xx-video.c:1723: warning: assignment discards qualifiers from pointer target type
/usr/src/v4l-dvb/v4l/em28xx-video.c:1735: warning: assignment discards qualifiers from pointer target type
  CC [M]  /usr/src/v4l-dvb/v4l/em28xx-i2c.o
  CC [M]  /usr/src/v4l-dvb/v4l/em28xx-cards.o
  CC [M]  /usr/src/v4l-dvb/v4l/em28xx-core.o
  CC [M]  /usr/src/v4l-dvb/v4l/em28xx-input.o
  CC [M]  /usr/src/v4l-dvb/v4l/et61x251_core.o
/usr/src/v4l-dvb/v4l/et61x251_core.c: In function 'et61x251_usb_probe':
/usr/src/v4l-dvb/v4l/et61x251_core.c:2570: warning: assignment discards qualifiers from pointer target type
  CC [M]  /usr/src/v4l-dvb/v4l/et61x251_tas5130d1b.o
  CC [M]  /usr/src/v4l-dvb/v4l/ir-functions.o
  CC [M]  /usr/src/v4l-dvb/v4l/ir-keymaps.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-audio.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-cards.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-controls.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-driver.o
/usr/src/v4l-dvb/v4l/ivtv-driver.c: In function 'ivtv_init_struct1':
/usr/src/v4l-dvb/v4l/ivtv-driver.c:625: warning: implicit declaration of function 'mutex_init'
/usr/src/v4l-dvb/v4l/ivtv-driver.c: In function 'ivtv_probe':
/usr/src/v4l-dvb/v4l/ivtv-driver.c:1170: error: 'IRQF_SHARED' undeclared (first use in this function)
/usr/src/v4l-dvb/v4l/ivtv-driver.c:1170: error: (Each undeclared identifier is reported only once
/usr/src/v4l-dvb/v4l/ivtv-driver.c:1170: error: for each function it appears in.)
/usr/src/v4l-dvb/v4l/ivtv-driver.c:1170: error: 'IRQF_DISABLED' undeclared (first use in this function)
make[3]: *** [/usr/src/v4l-dvb/v4l/ivtv-driver.o] Error 1
make[2]: *** [_module_/usr/src/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
make: *** [all] Error 2

Thanks!


-j4ni

---

### Post by LaLLi on 2007-04-24
I don't know if you got it working allready, but there is an update for the driver.
[http://www.linuxtv.org/pipermail/linux-dvb/2007-February/016291.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-February/016291.html)

You asked if kernel-headers and linux-headers is the same?
> #(in Ubuntu Edgy the headers package is called linux-headers-`uname -r`

---

