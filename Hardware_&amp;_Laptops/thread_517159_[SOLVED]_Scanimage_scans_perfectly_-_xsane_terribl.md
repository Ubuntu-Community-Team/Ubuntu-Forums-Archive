---
title: "[SOLVED] Scanimage scans perfectly - xsane terribly. Why? (Bearpaw 1200)"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by Nicksha on 2007-08-04
It's a Mustek Bearpaw 1200 scanner, and it's not being used very often, so I haven't paid much attention to a problem it had. In xsane scanned images are either too bright (sometimes completely white) or the contrast is too high, and there are vertical stripes in the image. I thought that the scanner has broken, since it is old, but just the other day I found out that there was some issue with the plustek backend, which has been resolved in the CVS. So i downloaded the deb package of the libsane CVS version from the [debian unstable]("http://packages.debian.org/unstable/libs/libsane") and copied libsane-plustek.so to the appropriate place. It worked! But only for scanimage, which now scans perfectly. Xsane still scans everything too bright, with high contrast and with stripes.

I unchecked options for automatic gamma and colour correction in the settings for xsane, but no change. I purged the xsane package and reinstalled it, and also cleared the .sane/xsane folder in home - no change. What else can I do? Maybe I need to copy something else from the libsane package, not just the backend driver?

---

### Post by david_e on 2007-08-04
Making applications work with a different version of theirs dynamic libraries is not a good idea. I suggest rebuilding xsane with the new libraries from source (using checkinstall for example) or using the debian unstable xsane package. Or using xsane and libsane from the ubuntu's repos.

---

### Post by Nicksha on 2007-08-04
I actually overwrote libsane-plustek.so.1.0.18 in /usr/lib/sane with the one from debian unstable (there are no multiple copies). It was the revision of the same version. I couldn't install the whole package because it complained about libc6 verson. Also, couldn't compile sane from source for some reason... I did this just to see if it works, and it did (for scanimage, at least). I know it's not the best solution, but whatever works...

The xsane and libsane in the ubuntu repos were the ones causing all the trouble. Someone suggested that going back to 1.0.15 version solved the problem for them, but packages.ubuntu.com only has packages from dapper (1.0.17) and newer.

---

### Post by david_e on 2007-08-04
If you don't want to recompile from source you could use the ldd command to see which libraries are linked to xsane and scanimage. Maybe there is some lib which xsane links and scanimage don't in the "libsane" package. Or maybe the problem is not linked to the scanner drivers, but there is some problem in the post-processing... (if they are linking the same libraries from sanelib then it can't be a driver issue in my opinion).

*** EDIT ***
Just do ldd /usr/bin/xsane and ldd /usr/bin/scanimage.

---

### Post by Nicksha on 2007-08-04
Yes, the post-processing makes sense. The ldd (good idea) command gave the following:

```

ldd /usr/bin/xsane
        linux-gate.so.1 =>  (0xffffe000)
        libsane.so.1 => /usr/lib/libsane.so.1 (0xb7eef000)
        libusb-0.1.so.4 => /lib/libusb-0.1.so.4 (0xb7ee7000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ecf000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ea8000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7e89000)
        libtiff.so.4 => /usr/lib/libtiff.so.4 (0xb7e37000)
        libieee1284.so.3 => /usr/lib/libieee1284.so.3 (0xb7e2d000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7e29000)
        libgimpui-2.0.so.0 => /usr/lib/libgimpui-2.0.so.0 (0xb7e19000)
        libgimpwidgets-2.0.so.0 => /usr/lib/libgimpwidgets-2.0.so.0 (0xb7d39000)
        libgimp-2.0.so.0 => /usr/lib/libgimp-2.0.so.0 (0xb7d0d000)
        libgimpmath-2.0.so.0 => /usr/lib/libgimpmath-2.0.so.0 (0xb7d08000)
        libgimpcolor-2.0.so.0 => /usr/lib/libgimpcolor-2.0.so.0 (0xb7cff000)
        libgimpbase-2.0.so.0 => /usr/lib/libgimpbase-2.0.so.0 (0xb7cf2000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7999000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7913000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb78f8000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb78e1000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb78d9000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb78ae000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb789f000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7897000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb7894000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb788c000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb7886000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb787d000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb7877000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7839000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb77c9000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb76d8000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb769e000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb769b000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7605000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb75e2000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb75ce000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb748d000)
        /lib/ld-linux.so.2 (0xb7f0c000)
        libgimpmodule-2.0.so.0 => /usr/lib/libgimpmodule-2.0.so.0 (0xb7489000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb745d000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb73f2000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb73d2000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb73cf000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb73c9000)

ldd /usr/bin/scanimage
        linux-gate.so.1 =>  (0xffffe000)
        libsane.so.1 => /usr/lib/libsane.so.1 (0xb7f65000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f61000)
        libusb-0.1.so.4 => /lib/libusb-0.1.so.4 (0xb7f58000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f41000)
        libtiff.so.4 => /usr/lib/libtiff.so.4 (0xb7eef000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7ed0000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7ebc000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e95000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d54000)
        libieee1284.so.3 => /usr/lib/libieee1284.so.3 (0xb7d49000)
        /lib/ld-linux.so.2 (0xb7f82000)


```

Of course, with the xsane being the GUI app, more libraries are linked, but I've noticed some that were Gimp-related (maybe it's nothing, because gimp can acquire pictures through xsane).

I don't know where to look for these post-processing settings. I've turned off all the autoenhance/autocorrect options in the setup window. And besides, I've got the same weird scan results with all GUI apps (kooka, xscanimage, quiteinsane), and command-line scanimage is OK, so maybe there's some system-wide setting for this... I'll try to find out what it could be.

---

### Post by Nicksha on 2007-08-04
OK, found it!

After some testing, in /etc/sane.d/plustek.conf the following settings worked:

option altCalibration 0
option skipCalibration 0
option skipFine 0
option skipFineWhite 1

The stupid part is, I think I messed this up myself when I first noticed what I know now was a bug in a backend, and tried to fix it by changing calibration values (back in april, I think). And now, when the bug has been corrected in the CVS, the changes I made were no longer required (only I couldn't remember making them). 

david_e, thank you for your support and tips!

---

