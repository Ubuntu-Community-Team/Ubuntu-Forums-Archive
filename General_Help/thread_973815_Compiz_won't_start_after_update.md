---
title: "Compiz won't start after update"
date: 2008-11-07
forum: General Help
---

### Post by El Lance-O on 2008-11-07
I've read the other threads with the same problem of Compiz not starting, but I have a different problem.

Here's the compiz_crash file that was created:

```
(no debugging symbols found)
Attaching to program: /usr/bin/compiz.real, process 11822
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
[New Thread 0xb6cebab0 (LWP 11822)]
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
Reading symbols from /usr/lib/compiz/libinotify.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libinotify.so
Reading symbols from /usr/lib/compiz/libpng.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libmblur.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmblur.so
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libgsf-1.so.114...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libgio-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /usr/lib/libpixman-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libxcb-render-util.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render-util.so.0
Reading symbols from /usr/lib/libxcb-render.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render.so.0
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/compiz/libannotate.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libannotate.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libplace.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libtext.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libshelf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshelf.so
Reading symbols from /usr/lib/compiz/libresize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libdbus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/compiz/libsession.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libwidget.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwidget.so
Reading symbols from /usr/lib/compiz/libwater.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwater.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libring.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libring.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libblur.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libblur.so
Reading symbols from /usr/lib/libGLU.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compiz/libglib.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/compiz/libclone.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libclone.so
Reading symbols from /usr/lib/compiz/libregex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libanimation.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/compiz/libwobbly.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libvideo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libfade.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libaddhelper.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libaddhelper.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libmag.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmag.so
Reading symbols from /usr/lib/compiz/libneg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libscale.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libshowmouse.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshowmouse.so
Reading symbols from /usr/lib/compiz/librotate.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /home/ellanceo/.compiz/plugins/libscreensaver.so...done.
Loaded symbols for /home/ellanceo/.compiz/plugins/libscreensaver.so
Reading symbols from /usr/lib/libXss.so.1...done.
Loaded symbols for /usr/lib/libXss.so.1
Reading symbols from /usr/lib/compiz/libgroup.so...done.
Loaded symbols for /usr/lib/compiz/libgroup.so
Reading symbols from /usr/lib/compiz/libexpo.so...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libezoom.so...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
0xb7fc6430 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread 0xb6cebab0 (LWP 11822)):
#0  0xb7fc6430 in __kernel_vsyscall ()
#1  0xb7b3c5e3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ad975b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5cb93d7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0xb7ed90f4 in _XEnq () from /usr/lib/libX11.so.6
#6  0xb7ee10c4 in ?? () from /usr/lib/libX11.so.6
#7  0xb7ee139a in _XReply () from /usr/lib/libX11.so.6
#8  0xb7ed4667 in XSync () from /usr/lib/libX11.so.6
#9  0x08054b29 in compCheckForError ()
#10 0x0805b709 in ?? ()
#11 0x0805bced in addScreenAction ()
#12 0x08076917 in ?? ()
#13 0x08077042 in ?? ()
#14 0x080773a2 in compInitDisplayOptionFromMetadata ()
#15 0x0807741e in compInitDisplayOptionsFromMetadata ()
#16 0xb4d596fc in ?? () from /usr/lib/compiz/libezoom.so
#17 0xb4d59003 in ?? () from /usr/lib/compiz/libezoom.so
#18 0x080715dd in ?? ()
#19 0x08053f2a in forEachDisplayObject ()
#20 0x080718c2 in ?? ()
#21 0x08052c53 in compObjectForEachType ()
#22 0x08071602 in ?? ()
#23 0x0807176d in pushPlugin ()
#24 0x080587e3 in eventLoop ()
#25 0x080528a7 in main ()
#0  0xb7fc6430 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xb7fc6430 in __kernel_vsyscall ()
#1  0xb7b3c5e3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ad975b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5cb93d7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0xb7ed90f4 in _XEnq () from /usr/lib/libX11.so.6
#6  0xb7ee10c4 in ?? () from /usr/lib/libX11.so.6
#7  0xb7ee139a in _XReply () from /usr/lib/libX11.so.6
#8  0xb7ed4667 in XSync () from /usr/lib/libX11.so.6
#9  0x08054b29 in compCheckForError ()
#10 0x0805b709 in ?? ()
#11 0x0805bced in addScreenAction ()
#12 0x08076917 in ?? ()
#13 0x08077042 in ?? ()
#14 0x080773a2 in compInitDisplayOptionFromMetadata ()
#15 0x0807741e in compInitDisplayOptionsFromMetadata ()
#16 0xb4d596fc in ?? () from /usr/lib/compiz/libezoom.so
#17 0xb4d59003 in ?? () from /usr/lib/compiz/libezoom.so
#18 0x080715dd in ?? ()
#19 0x08053f2a in forEachDisplayObject ()
#20 0x080718c2 in ?? ()
#21 0x08052c53 in compObjectForEachType ()
#22 0x08071602 in ?? ()
#23 0x0807176d in pushPlugin ()
#24 0x080587e3 in eventLoop ()
#25 0x080528a7 in main ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 11822
```

Also after this when trying to do 'compiz --replace' in a terminal, I get:

```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a8a7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a8a96e]
#2 /usr/lib/libX11.so.6 [0xb7ee0619]
#3 /usr/lib/libGL.so.1 [0xb7c95345]

```

---

### Post by El Lance-O on 2008-11-08
Nothing?

---

### Post by eternalnewbee on 2008-11-08
Hi there.
Check & see if compiz is still installed. Check if your Hardware Driver is enabled.
And take it from there.

---

### Post by El Lance-O on 2008-11-20
:lolflag:

Yes, compiz is installed, and my nvidia drivers are set up properly.

I managed to get compiz to start by resetting everything to default, but I get the window decoration problems that other have had. I think the majority of it from what it looks like is the extra plugins I installed.

I'm dreading a complete re-configuring of compiz, it's no fun making it perfect. :(

---

### Post by eternalnewbee on 2008-11-20
There's a **window decorator** plugin in **compiz manager**. Have you checked if it is enabled?
That solved it for me.
And I also run Emerald. No troubles there with window decorations.
Nice Avatar btw.

---

### Post by Izek on 2008-11-20
Have you tried installing **emerald** to get around the no decorations in compiz?

---

### Post by eternalnewbee on 2008-11-20
> Have you tried installing emerald to get around the no decorations in compiz?
Oops, double post:lolflag:

---

### Post by Izek on 2008-11-20
> **eternalnewbee said:**
> Oops, double post:lolflag:

posted it right as you were posting. Wish vbulletin could give that goofy phpBB error stating someone posted while you were posting.

---

### Post by eternalnewbee on 2008-11-20
> posted it right as you were posting. Wish vbulletin could give that goofy phpBB error stating someone posted while you were posting.
Better double than none;)

---

