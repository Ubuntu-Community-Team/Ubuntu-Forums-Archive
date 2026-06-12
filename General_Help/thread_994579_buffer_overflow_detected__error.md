---
title: "*** buffer overflow detected *** error"
date: 2008-11-26
forum: General Help
---

### Post by yinglcs2 on 2008-11-26
Hi,

I have a c++ application compiled using gcc on ubuntu 8.10. But i get this exception when i execute it.
Can you please tell me how can I trouble-shoot it?


*** buffer overflow detected ***: ./TestGtkEmbed terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7532558]
/lib/tls/i686/cmov/libc.so.6[0xb7530680]
/lib/tls/i686/cmov/libc.so.6[0xb7530de8]
./TestGtkEmbed[0x804f914]
./TestGtkEmbed[0x804f7c5]
./TestGtkEmbed[0x804bbd0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb744e685]
./TestGtkEmbed[0x8049f61]
======= Memory map: ========
08048000-08053000 r-xp 00000000 08:13 138785
/media/olddata/objdir/ss3/embedding/browser/gtk/tests/TestGtkEmbed
08053000-08054000 r-xp 0000a000 08:13 138785
/media/olddata/objdir/ss3/embedding/browser/gtk/tests/TestGtkEmbed
08054000-08055000 rwxp 0000b000 08:13 138785
/media/olddata/objdir/ss3/embedding/browser/gtk/tests/TestGtkEmbed
08d45000-08d88000 rwxp 08d45000 00:00 0          [heap]
b7180000-b7181000 rwxp b7180000 00:00 0
b7181000-b718b000 r-xp 00000000 08:21 779276
/lib/tls/i686/cmov/libnss_files-2.8.90.so
b718b000-b718c000 r-xp 00009000 08:21 779276
/lib/tls/i686/cmov/libnss_files-2.8.90.so
b718c000-b718d000 rwxp 0000a000 08:21 779276
/lib/tls/i686/cmov/libnss_files-2.8.90.so
b718d000-b7196000 r-xp 00000000 08:21 779360
/lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7196000-b7197000 r-xp 00008000 08:21 779360
/lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7197000-b7198000 rwxp 00009000 08:21 779360
/lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7198000-b71ad000 r-xp 00000000 08:21 779273
/lib/tls/i686/cmov/libnsl-2.8.90.so
b71ad000-b71ae000 r-xp 00014000 08:21 779273
/lib/tls/i686/cmov/libnsl-2.8.90.so
b71ae000-b71af000 rwxp 00015000 08:21 779273
/lib/tls/i686/cmov/libnsl-2.8.90.so
b71af000-b71b1000 rwxp b71af000 00:00 0
b71b1000-b71b8000 r-xp 00000000 08:21 779274
/lib/tls/i686/cmov/libnss_compat-2.8.90.so
b71b8000-b71b9000 r-xp 00006000 08:21 779274
/lib/tls/i686/cmov/libnss_compat-2.8.90.so
b71b9000-b71ba000 rwxp 00007000 08:21 779274
/lib/tls/i686/cmov/libnss_compat-2.8.90.so
b71ba000-b71f9000 r-xp 00000000 08:21 811455
/usr/lib/locale/en_US.utf8/LC_CTYPE
b71f9000-b71fa000 r-xp 00000000 08:21 811460
/usr/lib/locale/en_US.utf8/LC_NUMERIC
b71fa000-b71fb000 r-xp 00000000 08:21 811463
/usr/lib/locale/en_US.utf8/LC_TIME
b71fb000-b72dc000 r-xp 00000000 08:21 811454
/usr/lib/locale/en_US.utf8/LC_COLLATE
b72dc000-b72dd000 r-xp 00000000 08:21 811458
/usr/lib/locale/en_US.utf8/LC_MONETARY
b72dd000-b72de000 r-xp 00000000 08:21 811464
/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b72de000-b72df000 r-xp 00000000 08:21 811461
/usr/lib/locale/en_US.utf8/LC_PAPER
b72df000-b72e0000 r-xp 00000000 08:21 811459
/usr/lib/locale/en_US.utf8/LC_NAME
b72e0000-b72e1000 r-xp 00000000 08:21 811453
/usr/lib/locale/en_US.utf8/LC_ADDRESS
b72e1000-b72e2000 r-xp 00000000 08:21 811462
/usr/lib/locale/en_US.utf8/LC_TELEPHONE
b72e2000-b72e3000 r-xp 00000000 08:21 811457
/usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b72e3000-b72ea000 r-xs 00000000 08:21 788093
/usr/lib/gconv/gconv-modules.cache
b72ea000-b72eb000 r-xp 00000000 08:21 811456
/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b72eb000-b72ee000 rwxp b72eb000 00:00 0
b72ee000-b72f2000 r-xp 00000000 08:21 779610     /usr/lib/libXdmcp.so.6.0.0
b72f2000-b72f3000 rwxp 00003000 08:21 779610     /usr/lib/libXdmcp.so.6.0.0
b72f3000-b72f5000 r-xp 00000000 08:21 779606     /usr/lib/libXau.so.6.0.0
b72f5000-b72f6000 rwxp 00001000 08:21 779606     /usr/lib/libXau.so.6.0.0
b72f6000-b731e000 r-xp 00000000 08:21 761931     /lib/libpcre.so.3.12.1
b731e000-b731f000 r-xp 00027000 08:21 761931     /lib/libpcre.so.3.12.1
b731f000-b7320000 rwxp 00028000 08:21 761931     /lib/libpcre.so.3.12.1
b7320000-b7321000 rwxp b7320000 00:00 0
b7321000-b7327000 r-xp 00000000 08:21 780631     /usr/lib/libxcb-render.so.0.0.0
b7327000-b7328000 r-xp 00005000 08:21 780631     /usr/lib/libxcb-render.so.0.0.0
b7328000-b7329000 rwxp 00006000 08:21 780631     /usr/lib/libxcb-render.so.0.0.0
b7329000-b732c000 r-xp 00000000 08:21 780633
/usr/lib/libxcb-render-util.so.0.0.0
b732c000-b732d000 r-xp 00002000 08:21 780633
/usr/lib/libxcb-render-util.so.0.0.0
b732d000-b732e000 rwxp 00003000 08:21 780633
/usr/lib/libxcb-render-util.so.0.0.0
b732e000-b7352000 r-xp 00000000 08:21 778688     /usr/lib/libpng12.so.0.27.0
b7352000-b7354000 rwxp 00023000 08:21 778688     /usr/lib/libpng12.so.0.27.0
b7354000-b7393000 r-xp 00000000 08:21 780629     /usr/lib/libpixman-1.so.0.12.0
b7393000-b7395000 r-xp 0003e000 08:21 780629     /usr/lib/libpixman-1.so.0.12.0
b7395000-b7396000 rwxp 00040000 08:21 780629     /usr/lib/libpixman-1.so.0.12.0
b7396000-b73ae000 r-xp 00000000 08:21 762383     /lib/libselinux.so.1
b73ae000-b73af000 r-xp 00017000 08:21 762383     /lib/libselinux.so.1
b73af000-b73b0000 rwxp 00018000 08:21 762383     /lib/libselinux.so.1
b73b0000-b73b1000 rwxp b73b0000 00:00 0
b73b1000-b73b9000 r-xp 00000000 08:21 780989     /usr/lib/libXcursor.so.1.0.2
b73b9000-b73ba000 rwxp 00007000 08:21 780989     /usr/lib/libXcursor.so.1.0.2
b73ba000-b73bf000 r-xp 00000000 08:21 781470     /usr/lib/libXrandr.so.2.1.0
b73bf000-b73c0000 r-xp 00005000 08:21 781470     /usr/lib/libXrandr.so.2.1.0
b73c0000-b73c1000 rwxp 00006000 08:21 781470     /usr/lib/libXrandr.so.2.1.0
b73c1000-b73c9000 r-xp 00000000 08:21 781250     /usr/lib/libXi.so.6.0.0
b73c9000-b73ca000 r-xp 00007000 08:21 781250     /usr/lib/libXi.so.6.0.0
b73ca000-b73cb000 rwxp 00008000 08:21 781250     /usr/lib/libXi.so.6.0.0
b73cb000-b73cd000 r-xp 00000000 08:21 110340     /usr/lib/libXinerama.so.1.0.0
b73cd000-b73ce000 rwxp 00001000 08:21 110340     /usr/lib/libXinerama.so.1.0.0
b73ce000-b73d6000 r-xp 00000000 08:21 779856     /usr/lib/libXrender.so.1.3.0
b73d6000-b73d7000 r-xp 00007000 08:21 779856     /usr/lib/libXrender.so.1.3.0
b73d7000-b73d8000 rwxp 00008000 08:21 779856     /usr/lib/libXrender.so.1.3.0
b73d8000-b73d9000 rwxp b73d8000 00:00 0
b73d9000-b73e6000 r-xp 00000000 08:21 110065     /usr/lib/libXext.so.6.4.0
b73e6000-b73e8000 rwxp 0000c000 08:21 110065     /usr/lib/libXext.so.6.4.0
b73e8000-b740c000 r-xp 00000000 08:21 780896     /usr/lib/libexpat.so.1.5.2
b740c000-b740e000 r-xp 00023000 08:21 780896     /usr/lib/libexpat.so.1.5.2
b740e000-b740f000 rwxp 00025000 08:21 780896     /usr/lib/libexpat.so.1.5.2
b740f000-b7413000 r-xp 00000000 08:21 780999     /usr/lib/libXfixes.so.3.1.0
b7413000-b7414000 rwxp 00003000 08:21 780999     /usr/lib/libXfixes.so.3.1.0
b7414000-b7416000 r-xp 00000000 08:21 779904     /usr/lib/libXdamage.so.1.1.0
b7416000-b7417000 rwxp 00001000 08:21 779904     /usr/lib/libXdamage.so.1.1.0
b7417000-b7419000 r-xp 00000000 08:21 779806     /usr/lib/libXcomposite.so.1.0.0
b7419000-b741a000 r-xp 00001000 08:21 779806     /usr/lib/libXcomposite.so.1.0.0
b741a000-b741b000 rwxp 00002000 08:21 779806     /usr/lib/libXcomposite.so.1.0.0
b741b000-b741c000 rwxp b741b000 00:00 0
b741c000-b7433000 r-xp 00000000 08:21 779615     /usr/lib/libxcb.so.1.0.0
b7433000-b7434000 r-xp 00016000 08:21 779615     /usr/lib/libxcb.so.1.0.0
b7434000-b7435000 rwxp 00017000 08:21 779615     /usr/lib/libxcb.so.1.0.0
b7435000-b7436000 r-xp 00000000 08:21 779619     /usr/lib/libxcb-xlib.so.0.0.0
b7436000-b7437000 r-xp 00000000 08:21 779619     /usr/lib/libxcb-xlib.so.0.0.0
b7437000-b7438000 rwxp 00001000 08:21 779619     /usr/lib/libxcb-xlib.so.0.0.0
b7438000-b7590000 r-xp 00000000 08:21 779267
/lib/tls/i686/cmov/libc-2.8.90.so
b7590000-b7592000 r-xp 00158000 08:21 779267
/lib/tls/i686/cmov/libc-2.8.90.so
b7592000-b7593000 rwxp 0015a000 08:21 779267
/lib/tls/i686/cmov/libc-2.8.90.so
b7593000-b7596000 rwxp b7593000 00:00 0
b7596000-b75a3000 r-xp 00000000 08:21 761876     /lib/libgcc_s.so.1
b75a3000-b75a4000 r-xp 0000c000 08:21 761876     /lib/libgcc_s.so.1
b75a4000-b75a5000 rwxp 0000d000 08:21 761876     /lib/libgcc_s.so.1
b75a5000-b7688000 r-xp 00000000 08:21 110312     /usr/lib/libstdc++.so.6.0.10
b7688000-b7689000 ---p 000e3000 08:21 110312     /usr/lib/libstdc++.so.6.0.10
b7689000-b768d000 r-xp 000e3000 08:21 110312     /usr/lib/libstdc++.so.6.0.10
b768d000-b768e000 rwxp 000e7000 08:21 110312     /usr/lib/libstdc++.so.6.0.10
b768e000-b7694000 rwxp b768e000 00:00 0
b7694000-b7749000 r-xp 00000000 08:21 780462
/usr/lib/libglib-2.0.so.0.1800.2
b7749000-b774a000 r-xp 000b4000 08:21 780462
/usr/lib/libglib-2.0.so.0.1800.2
b774a000-b774b000 rwxp 000b5000 08:21 780462
/usr/lib/libglib-2.0.so.0.1800.2
b774b000-b774c000 rwxp b774b000 00:00 0
b774c000-b7788000 r-xp 00000000 08:21 780488
/usr/lib/libgobject-2.0.so.0.1800Aborted

---

