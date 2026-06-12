---
title: "Compiz Crashes Randomly"
date: 2008-09-05
forum: General Help
---

### Post by okeven on 2008-09-05
I just started having a problem with Compiz crashing.  I did not make any hardware or software changes to provoke it, it just started happening a week ago.  Can someone look at the compiz crash log and see if you can help me out?  Thanks a lot!

```
(no debugging symbols found)
Attaching to program: /usr/bin/compiz.real, process 6402
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
Reading symbols from /usr/lib/libgobject-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0xb6ef3a10 (LWP 6402)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libpcre.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpcre.so.3
Reading symbols from /lib/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libdbus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libplace.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libresize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/librsvg-2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libgio-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /usr/lib/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libstdc++.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /lib/libbz2.so.1.0...
(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/compiz/libimgjpeg.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libtext.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libvideo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libsnap.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsnap.so
Reading symbols from /usr/lib/compiz/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libscale.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libexpo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libswitcher.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libextrawm.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libfade.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libscaleaddon.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscaleaddon.so
Reading symbols from /usr/lib/compiz/libscalefilter.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscalefilter.so
Reading symbols from /usr/lib/compiz/libsession.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libshift.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libwobbly.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/librotate.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
(no debugging symbols found)
0xb7f0f410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread 0xb6ef3a10 (LWP 6402)):
#0  0xb7f0f410 in __kernel_vsyscall ()
#1  0xb7adb4d3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7a7e643 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb6d78c4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0xb59218c5 in ?? () from /usr/lib/compiz/libanimation.so
#6  0xb57e6e91 in ?? () from /usr/lib/compiz/libwobbly.so
#7  0xb5854dd5 in ?? () from /usr/lib/compiz/libfade.so
#8  0xb6d42a99 in ?? () from /usr/lib/compiz/libcube.so
#9  0xb590aeb5 in ?? () from /usr/lib/compiz/libexpo.so
#10 0xb587e9ab in ?? () from /usr/lib/compiz/libswitcher.so
#11 0xb6d51d82 in ?? () from /usr/lib/compiz/librotate.so
#12 0xb5912ce7 in ?? () from /usr/lib/compiz/libscale.so
#13 0x080583ee in eventLoop ()
#14 0x080528bc in main ()
#0  0xb7f0f410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xb7f0f410 in __kernel_vsyscall ()
#1  0xb7adb4d3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7a7e643 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb6d78c4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0xb59218c5 in ?? () from /usr/lib/compiz/libanimation.so
#6  0xb57e6e91 in ?? () from /usr/lib/compiz/libwobbly.so
#7  0xb5854dd5 in ?? () from /usr/lib/compiz/libfade.so
#8  0xb6d42a99 in ?? () from /usr/lib/compiz/libcube.so
#9  0xb590aeb5 in ?? () from /usr/lib/compiz/libexpo.so
#10 0xb587e9ab in ?? () from /usr/lib/compiz/libswitcher.so
#11 0xb6d51d82 in ?? () from /usr/lib/compiz/librotate.so
#12 0xb5912ce7 in ?? () from /usr/lib/compiz/libscale.so
#13 0x080583ee in eventLoop ()
#14 0x080528bc in main ()
```
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 6402

---

### Post by overdrank on 2008-09-05
Hi and could you tell us some system specs?

---

### Post by okeven on 2008-09-05
Intel Core 2 2.183 GHZ
Nvidia 8600
2 GB Ram
Ubuntu 8.04

Need anything else?

---

### Post by overdrank on 2008-09-05
> **okeven said:**
> Intel Core 2 2.183 GHZ
Nvidia 8600
2 GB Ram
Ubuntu 8.04

Need anything else?

Ok how did you install the nvidia driver and which one? :)

---

### Post by okeven on 2008-09-06
I do not remember ever installing an Nvidia driver.  How would I check?

---

### Post by overdrank on 2008-09-06
> **okeven said:**
> I do not remember ever installing an Nvidia driver.  How would I check?

Ok you can look under system, administration, hardware drivers.

---

### Post by sayakb on 2008-09-06
Try compiz-check: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by okeven on 2008-09-06
OK.  The driver I am using says NVIDIA accelerated graphics driver (latest cards).  Is that the correct one?

---

### Post by okeven on 2008-09-06
> **LinuxIsInnovation said:**
> Try compiz-check: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

compiz-check gave me all OK's.  Does the crash log mean anything?

---

### Post by okeven on 2008-09-08
Anybody?  Please?

---

### Post by Kevbert on 2008-09-08
Please perform a memory check (memtest from the boot menu).

---

### Post by okeven on 2008-09-08
Already did that based on another persons suggestion twice.  Passed just fine.  Thanks for the suggestion!  Can you think of anything else?  Do you know how to decipher the error log?

---

