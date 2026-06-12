---
title: "Can't set up Panasonic printer: libgs is too old"
date: 2016-05-04
forum: Hardware
---

### Post by Roman_Grachev on 2016-05-04
Hi

I'm installing drivers for my Panasonic printer/scanner (KX-MB1520) using this manual: [http://panasonic.net/pcc/support/fax/common/table/linuxdriver.html](http://panasonic.net/pcc/support/fax/common/table/linuxdriver.html)
It worked all right all previous Ubuntu and SUSE installations, but right now, on Kubuntu 16.04 it doesn't.
After I perform all the steps and see my device in printers list, I try to print something but always see this error message in print queue:

> (PID 2130) Cannot load libgs or libgs version too old then 8.0

I tried to install ghostscript and libgs9 manually but it seems that I have them both up to date (GPL Ghostscript 9.18 (2015-10-05)). So I don't know what to try to fix it, any help appreciated.

Thanks!

---

### Post by Roman_Grachev on 2016-05-04
Apparently the driver expected libgs.so to be in /usr/lib while it was actually residing in /usr/lib/x86_64-linux-gnu
So
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libgs.so.9 /usr/lib/libgs.so
```
did the trick.

---

### Post by mkdugi on 2016-07-07
Hi,

This problem is not solved.
Besides libgs problem there is one more.
There is filter program - L_H0JDGCZAZ. And it crashes:

D [07/Jul/2016:20:46:31 +0200] [Job 61] PID 2608 (/usr/lib/cups/filter/L_H0JDGCZAZ) crashed on signal 11.


```
~$ /usr/lib/cups/filter/L_H0JDGCZAZ
DEBUG: (PID 23238) Start Panasonic GDI filter on /usr/lib/cups/filter/L_H0JDGCZAZ
ERROR: (PID 23238) Usage: /usr/lib/cups/filter/L_H0JDGCZAZ job user title copies options [filename]
Segmentation fault (core dumped)
```

```
 [ 3967.356876] L_H0JDGCZAZ[23238]: segfault at 710 ip 000000000040ad4a sp 00007ffe53f613e0 error 4 in L_H0JDGCZAZ[400000+8c000]
```
```
~$ ldd /usr/lib/cups/filter/L_H0JDGCZAZ
    linux-vdso.so.1 =>  (0x00007ffe93ff0000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f52444e4000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f52442e0000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f5243f5d000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f5243c54000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f5243a3e000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f5243674000)
    /lib64/ld-linux-x86-64.so.2 (0x0000558a22494000)

```

---

### Post by maciek6 on 2016-08-30
Hi
Anyone got some solution on this?
I have exactly the same problem, the Panasonic KX-MB2545 has been working ok on ubuntu 14.04 (32bit), but when I switched to 16.04 (32bit) I encounter the same problem, especially with filter program:

/usr/lib/cups/filter/L_H0JDGCZAZ
DEBUG: (PID 6818) Start Panasonic GDI filter on /usr/lib/cups/filter/L_H0JDGCZAZ
ERROR: (PID 6818) Usage: /usr/lib/cups/filter/L_H0JDGCZAZ job user title copies options [filename]

---

### Post by leopoldo-vaghi on 2016-12-29
> **Roman_Grachev said:**
> Apparently the driver expected libgs.so to be in /usr/lib while it was actually residing in /usr/lib/x86_64-linux-gnu
So
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libgs.so.9 /usr/lib/libgs.so
```
did the trick.

This worked for me, THANS!

---

### Post by gus99 on 2017-02-16
Thanks, it works for me also :-)

>> [COLOR=#000000][FONT=&quot]sudo ln -s /usr/lib/x86_64-linux-gnu/libgs.so.9 /usr/lib/libgs.so[/FONT][/COLOR]

---

