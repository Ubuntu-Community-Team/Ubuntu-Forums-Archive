---
title: "Lifeview Flyvideo FM2000 Cannot install"
date: 2012-10-14
forum: Hardware
---

### Post by sinombre5 on 2012-10-14
HI Guys
I got a problem installing
LIfeVIew Flyvideo Fm 2000 on Ubuntu 10.04 x64bits
Details:
[http://www.lifeview.com.tw/html/products/internal_tv/flytv_prime30.htm](http://www.lifeview.com.tw/html/products/internal_tv/flytv_prime30.htm)

Lspci
02:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

dmesg | grep saa
N/A

WHAT I HAVE DONE TO TRY TO INSTALL THE TV TUNE
1.Update the kernel
uname -r
3.6.2

2-Update the v4l
sudo apt-get install mercurial
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvd
sudo make
i got this error:
make -C /home/nicola/Escritorio/v4l-dvb/v4l 
make[1]: se ingresa al directorio «/home/nicola/Escritorio/v4l-dvb/v4l»
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/nicola/Escritorio/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/nicola/Escritorio/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/nicola/Escritorio/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/nicola/Escritorio/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/3.6.2/build
make -C /lib/modules/3.6.2/build SUBDIRS=/home/nicola/Escritorio/v4l-dvb/v4l CFLAGS="-I../linux/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
make[2]: Entering directory `/usr/src/linux-3.6.2'
  CC [M]  /home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.o
In file included from /home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.h:10,
                 from /home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:22:
/home/nicola/Escritorio/v4l-dvb/v4l/dvb_frontend.h:49: error: field 'parameters' has incomplete type
/home/nicola/Escritorio/v4l-dvb/v4l/dvb_frontend.h:313: error: array type has incomplete element type
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c: In function 'xc2028_set_params':
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1081: error: 'fe_bandwidth_t' undeclared (first use in this function)
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1081: error: (Each undeclared identifier is reported only once
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1081: error: for each function it appears in.)
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1081: error: expected ';' before 'bw'
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1082: warning: ISO C90 forbids mixed declarations and code
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1088: error: 'bw' undeclared (first use in this function)
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1088: error: dereferencing pointer to incomplete type
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1094: error: 'BANDWIDTH_6_MHZ' undeclared (first use in this function)
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1108: error: 'BANDWIDTH_8_MHZ' undeclared (first use in this function)
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1109: error: dereferencing pointer to incomplete type
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1116: error: 'BANDWIDTH_7_MHZ' undeclared (first use in this function)
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1117: error: dereferencing pointer to incomplete type
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1177: error: dereferencing pointer to incomplete type
/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.c:1178: error: 'T_DIGITAL_TV' undeclared (first use in this function)
make[3]: *** [/home/nicola/Escritorio/v4l-dvb/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/nicola/Escritorio/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-3.6.2'
make[1]: *** [default] Error 2
make[1]: se sale del directorio «/home/nicola/Escritorio/v4l-dvb/v4l»
make: *** [all] Error 2

I got stuck right there.

Any Help?

I apologize for being a newbie in linux.
I will really apreciate all your help.

My Regards.

---

