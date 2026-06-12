---
title: "Cant't install ATI driver on my T43 BH1"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by Wayne.wr on 2006-05-02
I followed the "Method 2" in the "Ubuntu Breezy Installation Guide"([http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide")) to install the newer 8.24.8 drivers, "ATI Radeon X300 Driver", on my T43-BH1.
But I **can't** create .deb packages. I got some error message as follows, after excuting the cmd
"LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy".

Error Messages
    dpkg: /usr/i386-linux/lib/libc.so.6 not found. 
   dpkg: /usr/i386-linux/lib/libXext.so.6 not found. 
   dpkg: /usr/i386-linux/lib/libX11.so.6 not found. 
   dpkg: /usr/i386-linux/lib/libpthread.so.0 not found.
   dpkg: /usr/i386-linux/lib/libdl.so.2 not found.
   dpkg: /usr/i386-linux/lib/libm.so.6 not found.
   dpkg: /usr/i386-linux/lib/libstdc++.so.5 not found.
   dpkg: /usr/i386-linux/lib/librt.so.1 not found.
   dpkg: /usr/i386-linux/lib/libGL.so.1 not found.
   dpkg: /usr/i386-linux/lib/libfglrx_gamma.so.1 not found.
   dpkg: /usr/i386-linux/lib/libfglrx_pp.so.1 not found.
   dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
   dh_shlibdeps: command returned error code 256
   make: *** [binary] Error 1
   make: Leaving directory `/tmp/fglrx' 

There's no such directory, /usr/i386-linux, in my system at all.

---

