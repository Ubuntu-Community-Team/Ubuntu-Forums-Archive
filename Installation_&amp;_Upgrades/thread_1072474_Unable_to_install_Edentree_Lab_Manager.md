---
title: "Unable to install Edentree Lab Manager"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by malikons on 2009-02-17
Hi fellows,

I am trying to install a 3rd party application Edentree Lab Manager on Ubuntu. It is supposed to be only for RHEL but I am wondering if someone here could help me installing it. I am running Ubuntu 8.10 (gnome) on HP mini-2133.

When I try to launch the application, below is what I get:

```
george@george-laptop:~/lmclient$ ./run-client.sh 
Xlib:  extension "RANDR" missing on display ":0.0".
Feb 17 17:47:18 DEBUG:::Client GUI Instantiated
*** glibc detected *** ./ClientGui: munmap_chunk(): invalid pointer: 0x09d86510 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e00454]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb6e2bc06]
/home/george/lmclient/libwx_gtk2-2.6.so.0[0xb76b92e3]
/home/george/lmclient/libwx_gtk2-2.6.so.0(_ZN8wxButton10SetDefaultEv+0x5f)[0xb76b9767]
/home/shiraz/lmclient/wx._controls_.so[0xb67dc37d]
./ClientGui(PyCFunction_Call+0x8e)[0x80fa0f2]
./ClientGui(PyObject_Call+0x28)[0x8059a00]
./ClientGui(PyEval_EvalFrame+0x3b25)[0x80a63fd]
./ClientGui(PyEval_EvalCodeEx+0x618)[0x80a9b4c]
./ClientGui(PyEval_EvalFrame+0x4e4f)[0x80a7727]
./ClientGui(PyEval_EvalCodeEx+0x618)[0x80a9b4c]
./ClientGui[0x80f9a74]
./ClientGui(PyObject_Call+0x28)[0x8059a00]
./ClientGui[0x80623e1]
./ClientGui(PyObject_Call+0x28)[0x8059a00]
./ClientGui[0x8089e60]
./ClientGui[0x8082fdf]
./ClientGui(PyObject_Call+0x28)[0x8059a00]
./ClientGui(PyEval_EvalFrame+0x1468)[0x80a3d40]
./ClientGui(PyEval_EvalCodeEx+0x618)[0x80a9b4c]
./ClientGui(PyEval_EvalFrame+0x4e4f)[0x80a7727]
./ClientGui(PyEval_EvalFrame+0x6b44)[0x80a941c]
./ClientGui(PyEval_EvalCodeEx+0x618)[0x80a9b4c]
./ClientGui(PyEval_EvalCode+0x2f)[0x80a9cf3]
./ClientGui(PyEval_EvalFrame+0x6a44)[0x80a931c]
./ClientGui(PyEval_EvalCodeEx+0x618)[0x80a9b4c]
./ClientGui(PyEval_EvalCode+0x2f)[0x80a9cf3]
./ClientGui(main+0x70f)[0x8055b43]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7da7685]
./ClientGui[0x80553ad]
======= Memory map: ========
08048000-08117000 r-xp 00000000 08:01 4547244    /home/george/lmclient/ClientGui
08117000-0813e000 rw-p 000cf000 08:01 4547244    /home/george/lmclient/ClientGui
0813e000-08143000 rw-p 0813e000 00:00 0 
09198000-09f04000 rw-p 09198000 00:00 0          [heap]
b4e0c000-b4f41000 r-xp 00000000 08:01 1369754    /usr/lib/libxml2.so.2.6.32
b4f41000-b4f42000 ---p 00135000 08:01 1369754    /usr/lib/libxml2.so.2.6.32
b4f42000-b4f46000 r--p 00135000 08:01 1369754    /usr/lib/libxml2.so.2.6.32
b4f46000-b4f47000 rw-p 00139000 08:01 1369754    /usr/lib/libxml2.so.2.6.32
b4f47000-b4f48000 rw-p b4f47000 00:00 0 
b4f48000-b4f79000 r-xp 00000000 08:01 1370875    /usr/lib/libcroco-0.6.so.3.0.1
b4f79000-b4f7c000 rw-p 00030000 08:01 1370875    /usr/lib/libcroco-0.6.so.3.0.1
b4f7c000-b4f89000 r-xp 00000000 08:01 1368200    /usr/lib/libgvfscommon.so.0.0.0
b4f89000-b4f8a000 r--p 0000d000 08:01 1368200    /usr/lib/libgvfscommon.so.0.0.0
b4f8a000-b4f8b000 rw-p 0000e000 08:01 1368200    /usr/lib/libgvfscommon.so.0.0.0
b4f8b000-b4fa3000 r-xp 00000000 08:01 1392645    /usr/lib/gio/modules/libgvfsdbus.so
b4fa3000-b4fa4000 r--p 00017000 08:01 1392645    /usr/lib/gio/modules/libgvfsdbus.so
b4fa4000-b4fa5000 rw-p 00018000 08:01 1392645    /usr/lib/gio/modules/libgvfsdbus.so
b4fa5000-b4fdb000 r-xp 00000000 08:01 270388     /lib/libdbus-1.so.3.4.0
b4fdb000-b4fdc000 r--p 00035000 08:01 270388     /lib/libdbus-1.so.3.4.0
b4fdc000-b4fdd000 rw-p 00036000 08:01 270388     /lib/libdbus-1.so.3.4.0
b4fea000-b4ff9000 r-xp 00000000 08:01 270374     /lib/libbz2.so.1.0.4
b4ff9000-b4ffa000 r--p 0000f000 08:01 270374     /lib/libbz2.so.1.0.4
b4ffa000-b4ffb000 rw-p 00010000 08:01 270374     /lib/libbz2.so.1.0.4
b4ffb000-b502b000 r-xp 00000000 08:01 1371152    /usr/lib/libgsf-1.so.114.0.8
b502b000-b502d000 r--p 0002f000 08:01 1371152    /usr/lib/libgsf-1.so.114.0.8
b502d000-b502e000 rw-p 00031000 08:01 1371152    /usr/lib/libgsf-1.so.114.0.8
b502e000-b502f000 rw-p b502e000 00:00 0 
b502f000-b5060000 r-xp 00000000 08:01 1371514    /usr/lib/librsvg-2.so.2.22.3
b5060000-b5061000 r--p 00030000 08:01 1371514    /usr/lib/librsvg-2.so.2.22.3
b5061000-b5062000 rw-p 00031000 08:01 1371514    /usr/lib/librsvg-2.so.2.22.3
b5070000-b5071000 r-xp 00000000 08:01 1394162    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5071000-b5072000 r--p 00000000 08:01 1394162    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5072000-b5073000 rw-p 00001000 08:01 1394162    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5073000-b5077000 r-xp 00000000 08:01 1394154    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5077000-b5078000 r--p 00003000 08:01 1394154  Aborted
george@george-laptop:~/lmclient$ 
```

Thank you.

---

