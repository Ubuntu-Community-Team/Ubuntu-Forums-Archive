---
title: "Compiz Keeps Crashing"
date: 2008-11-24
forum: General Help
---

### Post by joey-elijah on 2008-11-24
I installed XFCE and KDE4.1 alongside my beloved Gnome earlier, and everything was working fine.

Then, in a separate gnome session running netbook remix (but on  a dekstop, try it, it's lush!), the screen kept flickering. Obviously, i didn't quite notice what it was crashing in NBR as compiz isn't really needed.

back in my de facto desktop, i was greeted by pixelated screenlets, no AWN dock and butt ugly themes. 

I checked drivers - activated and fine.
renabled compiz and everything was fine.... then it crashed again.

I can keep repeating this, but what is making it crash?! 

Compiz Crash Handler gave me this: -

```
(no debugging symbols found)
Attaching to program: /usr/bin/compiz.real, process 9074
Reading symbols from /usr/lib/libX11-xcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11-xcb.so.1
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libxcb.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXext.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /usr/lib/libxcb-xlib.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-xlib.so.0
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/libXrender.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libGLcore.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /lib/ld-linux.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/compiz/libccp.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libdbus-glib-1.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-glib-1.so.2
Reading symbols from /lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libdbus-1.so.3
Reading symbols from /usr/lib/libgobject-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0xb6c2aab0 (LWP 9074)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /lib/libpcre.so.3...
(no debugging symbols found)...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libvpswitch.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libdbus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/compiz/libtext.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libpng12.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libxcb-render-util.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render-util.so.0
Reading symbols from /usr/lib/libxcb-render.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render.so.0
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libmousepoll.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libresize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libneg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libpng.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libvideo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libextrawm.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libsession.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/librsvg-2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libgio-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /lib/libselinux.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/compiz/libshift.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libdecoration.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libsnap.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsnap.so
Reading symbols from /usr/lib/compiz/libanimation.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/libstdc++.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compiz/libanimationaddon.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimationaddon.so
Reading symbols from /usr/lib/compiz/libobs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libobs.so
Reading symbols from /usr/lib/compiz/libwobbly.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libfade.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libmove.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/lib3d.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/lib3d.so
Reading symbols from /usr/lib/compiz/libscale.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libscalefilter.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscalefilter.so
Reading symbols from /usr/lib/compiz/librotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libcubeaddon.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcubeaddon.so
Reading symbols from /usr/lib/compiz/libscaleaddon.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscaleaddon.so
Reading symbols from /usr/lib/compiz/libexpo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libezoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/compiz/libswitcher.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
Reading symbols from /usr/lib/compiz/libloginout.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libloginout.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
(no debugging symbols found)
0xb7f09430 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread 0xb6c2aab0 (LWP 9074)):
#0  0xb7f09430 in __kernel_vsyscall ()
#1  0xb7a7b5e3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7a1875b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb6ac83d7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0x08069d8d in handleEvent ()
#6  0xb5b748a5 in ?? () from /usr/lib/compiz/libvpswitch.so
#7  0xb5b689d8 in ?? () from /usr/lib/compiz/libresize.so
#8  0xb5b5b8cd in ?? () from /usr/lib/compiz/libresizeinfo.so
#9  0xb591d76d in ?? () from /usr/lib/compiz/libvideo.so
#10 0xb58ebb84 in ?? () from /usr/lib/compiz/libextrawm.so
#11 0xb58e75c1 in ?? () from /usr/lib/compiz/libregex.so
#12 0xb58e2659 in ?? () from /usr/lib/compiz/libsession.so
#13 0xb58dc95d in ?? () from /usr/lib/compiz/libworkarounds.so
#14 0xb58cb8c4 in ?? () from /usr/lib/compiz/libshift.so
#15 0xb58bea9d in ?? () from /usr/lib/compiz/libdecoration.so
#16 0xb57252e5 in ?? () from /usr/lib/compiz/libsnap.so
#17 0xb571a8db in ?? () from /usr/lib/compiz/libanimation.so
#18 0xb558179e in ?? () from /usr/lib/compiz/libwobbly.so
#19 0xb56f7250 in ?? () from /usr/lib/compiz/libfade.so
#20 0xb557973d in ?? () from /usr/lib/compiz/libmove.so
#21 0xb4d90418 in ?? () from /usr/lib/compiz/libscale.so
#22 0xb4d875a6 in ?? () from /usr/lib/compiz/libscalefilter.so
#23 0xb4d398e6 in ?? () from /usr/lib/compiz/librotate.so
#24 0xb4938fc1 in ?? () from /usr/lib/compiz/libscaleaddon.so
#25 0xb492f1c0 in ?? () from /usr/lib/compiz/libexpo.so
#26 0xb4922a57 in ?? () from /usr/lib/compiz/libezoom.so
#27 0xb491b42e in ?? () from /usr/lib/compiz/libswitcher.so
#28 0x08057e4b in eventLoop ()
#29 0x080528a7 in main ()
#0  0xb7f09430 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xb7f09430 in __kernel_vsyscall ()
#1  0xb7a7b5e3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7a1875b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb6ac83d7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0x08069d8d in handleEvent ()
#6  0xb5b748a5 in ?? () from /usr/lib/compiz/libvpswitch.so
#7  0xb5b689d8 in ?? () from /usr/lib/compiz/libresize.so
#8  0xb5b5b8cd in ?? () from /usr/lib/compiz/libresizeinfo.so
#9  0xb591d76d in ?? () from /usr/lib/compiz/libvideo.so
#10 0xb58ebb84 in ?? () from /usr/lib/compiz/libextrawm.so
#11 0xb58e75c1 in ?? () from /usr/lib/compiz/libregex.so
#12 0xb58e2659 in ?? () from /usr/lib/compiz/libsession.so
#13 0xb58dc95d in ?? () from /usr/lib/compiz/libworkarounds.so
#14 0xb58cb8c4 in ?? () from /usr/lib/compiz/libshift.so
#15 0xb58bea9d in ?? () from /usr/lib/compiz/libdecoration.so
#16 0xb57252e5 in ?? () from /usr/lib/compiz/libsnap.so
#17 0xb571a8db in ?? () from /usr/lib/compiz/libanimation.so
#18 0xb558179e in ?? () from /usr/lib/compiz/libwobbly.so
#19 0xb56f7250 in ?? () from /usr/lib/compiz/libfade.so
#20 0xb557973d in ?? () from /usr/lib/compiz/libmove.so
#21 0xb4d90418 in ?? () from /usr/lib/compiz/libscale.so
#22 0xb4d875a6 in ?? () from /usr/lib/compiz/libscalefilter.so
#23 0xb4d398e6 in ?? () from /usr/lib/compiz/librotate.so
#24 0xb4938fc1 in ?? () from /usr/lib/compiz/libscaleaddon.so
#25 0xb492f1c0 in ?? () from /usr/lib/compiz/libexpo.so
#26 0xb4922a57 in ?? () from /usr/lib/compiz/libezoom.so
#27 0xb491b42e in ?? () from /usr/lib/compiz/libswitcher.so
#28 0x08057e4b in eventLoop ()
#29 0x080528a7 in main ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 9074
```

:confused:

---

