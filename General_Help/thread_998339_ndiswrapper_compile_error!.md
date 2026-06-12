---
title: "ndiswrapper compile error!"
date: 2008-11-30
forum: General Help
---

### Post by nevercroft on 2008-11-30
I'm compiling ndiswrapper-1.53 in Intrepid, I must compile it and not get it from the repositories because of this bug:

[http://forums.debian.net/viewtopic.php?p=100586&sid=f09bad1b17b5f4c62f1c4e68d044b8bf](http://forums.debian.net/viewtopic.php?p=100586&sid=f09bad1b17b5f4c62f1c4e68d044b8bf) involving "ndiwrapper.ko" not being created.

Whenever I run "make" I get this long line of errors:

```

groff@groff-desktop:~/Desktop/ndiswrapper-1.53$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
groff@groff-desktop:~/Desktop/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/groff/Desktop/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/groff/Desktop/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/groff/Desktop/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/groff/Desktop/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/groff/Desktop/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/groff/Desktop/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/groff/Desktop/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/groff/Desktop/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/groff/Desktop/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/groff/Desktop/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/groff/Desktop/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/groff/Desktop/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.o
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/groff/Desktop/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/groff/Desktop/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/groff/Desktop/ndiswrapper-1.53/driver'
make: *** [all] Error 2
groff@groff-desktop:~/Desktop/ndiswrapper-1.53$ 

```

Can anyone help me with this?

---

### Post by 80aless on 2008-12-02
check this
[HTML]http://ph.ubuntuforums.com/showthread.php?p=6115739[/HTML]

---

### Post by XaTriX on 2008-12-24
Link seems to be dead.

XaT

---

### Post by Neuroshock on 2009-01-07
I am running Ubuntu Intrepid and I came across the same error, trying to compile ndiswrapper 1.52. 
```
make[3]: *** [/root/ndiswrapper-1.52/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/root/ndiswrapper-1.52/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/ndiswrapper-1.52/driver'
make: *** [install] Error 2

```

I tried again after installing the linux kernel headers for dev., but with no success. Help!

---

