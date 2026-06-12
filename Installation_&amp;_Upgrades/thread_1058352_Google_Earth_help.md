---
title: "Google Earth help"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by bitf on 2009-02-02
Seeing as the FSF has yet to even start on a Google Earth viewer, and Marble, while a good piece of software, dosen't have all that I need, I was forced to use Google Earth.

I was able to get GE 4.2 working okay in 8.04, but in 8.10 in boots up than crashes. Is their a way to get it working?

---

### Post by taurus on 2009-02-02
How did you install it?  Have you tried starting it from a terminal to see what the error message is?

---

### Post by milesinnz on 2009-02-02
I have the same problem to, so here is a copy of the crash message.


wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  ./googleearth-bin [0x8058399]
  [0xf7fa0400]
  /lib32/libc.so.6 [0xf60bb882]
  /lib32/libc.so.6 [0xf60bcc97]
  /lib32/libc.so.6 [0xf60beb66]
  /lib32/libc.so.6(realloc+0x106) [0xf60bf9a6]
  ./libIGCore.so(_ZN3Gap4Core14igSystemMemory13systemReallocEPvj+0x24) [0xf68bca94]
  ./libIGCore.so(_ZN3Gap4Core18igMallocMemoryPool7reallocEPNS0_8igMemoryEj+0x138) [0xf68c9f88]
  ./libIGCore.so(_ZN3Gap4Core8igMemory9igReallocEPS1_j+0x63) [0xf68c5eb3]
  ./libIGCore.so(_ZN3Gap4Core8igMemory9igReallocEPvj+0x24) [0xf68c60d4]
  ./libIGGfx.so(_ZN3Gap3Gfx9ArrayListINS0_7TextureEE14getFreeElementEi+0x63) [0xf68227b3]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext21internalCreateTextureEiiNS0_21IG_GFX_TEXTURE_FORMATENS0_21IG_GFX_TEXTURE_SOURCEEjjb+0x47) [0xf67f68f7]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext13createTextureEiiNS0_21IG_GFX_TEXTURE_FORMATENS0_21IG_GFX_TEXTURE_SOURCEEjj+0x4d) [0xf67f6ccd]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll7Texture17syncCreateTextureERN3Gap3Gfx11igImageListE+0xade) [0xf2b2ce20]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll17SyncCreateTexture7executeEv+0x23) [0xf2b33423]
  ./libbase.so(_ZN5earth5Timer7executeERNS0_10SyncMethodEb+0x2a) [0xf7f35a32]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll17SyncCreateTexture6CreateERNS0_7TextureEPN3Gap3Gfx7igImageEPNS4_5Attrs13igTextureAttrE+0x45) [0xf2b328b3]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll7Texture12ProcessWorkQEd+0xfe) [0xf2b2f8f8]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll7Texture8endFrameEd+0x1a) [0xf2b3dc60]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll13VisualContext8endFrameEv+0x148) [0xf2b3ba94]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0xb2) [0xf2b3d9f8]
  /home/miles/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0xa1) [0xf2af7b51]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x24) [0xf62cd7d0]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x14) [0xf62ba60c]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xf7f359bb]
  ./libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xf6da9fc2]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xf6d3e9a1]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xf6d3f4af]
  ./libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xf6d3243d]
  ./libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xf6ce424b]
  ./libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0xc3) [0xf6d58503]
  ./libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26) [0xf6d583e6]
  ./libqt-mt.so.3(_ZN12QApplication4execEv+0x1f) [0xf6d3e39f]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEv+0x24f) [0xf76dd821]
  ./googleearth-bin(main+0x11f) [0x8058817]
  /lib32/libc.so.6(__libc_start_main+0xe5) [0xf6061685]
  ./googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]

---

### Post by bitf on 2009-02-02
"google earth has caught signal 11" seems to be key

---

### Post by milesinnz on 2009-02-02
This worked for me


[http://blog.mymediasystem.net/uncategorized/google-earth-crashes/](http://blog.mymediasystem.net/uncategorized/google-earth-crashes/)

but had also to use the line

ln -s ~/.googleearth/libGL.so.1.2 /usr/lib32/libGL.so.1
googleearth


Haven't a clue why?! but it works so far, at least it has not crashed yet

---

### Post by bitf on 2009-02-02
> **milesinnz said:**
> This worked for me


[http://blog.mymediasystem.net/uncategorized/google-earth-crashes/](http://blog.mymediasystem.net/uncategorized/google-earth-crashes/)

but had also to use the line

ln -s ~/.googleearth/libGL.so.1.2 /usr/lib32/libGL.so.1
googleearth


Haven't a clue why?! but it works so far, at least it has not crashed yet
No luck, thanks anyway.

---

### Post by milesinnz on 2009-02-02
Sorry, but did you execute the below line before the other one (line is my previous post)? Is in the web page reference I included in my previous posting

cd ~/.googleearth
wget [http://mymediasystem.net/wp/2009/01/libGL.so.1.2](http://mymediasystem.net/wp/2009/01/libGL.so.1.2)
googleearth

---

### Post by bitf on 2009-02-02
> **milesinnz said:**
> Sorry, but did you execute the below line before the other one (line is my previous post)? Is in the web page reference I included in my previous posting

cd ~/.googleearth
wget [http://mymediasystem.net/wp/2009/01/libGL.so.1.2](http://mymediasystem.net/wp/2009/01/libGL.so.1.2)
googleearth
yes

---

### Post by milesinnz on 2009-02-02
Sorry I can't be much more help. Would be interesting to see if you had the same sort of error messages as I originally did.

You can get the execution line from right clicking the Google Earth icon, and then copy and then paste the command line into a terminal screen if you haven't already done that.

---

### Post by jman82s on 2009-02-02
I was having this problem on Gutsy (upgraded to Intrepid last night) and Fedora 10. If you install the latest version of GE, 4.3, the problem goes away. However, the font rendering is kinda screwy. I managed to fix it on Fedora, but I forget what exactly I did.

---

### Post by bitf on 2009-02-04
> **jman82s said:**
> I was having this problem on Gutsy (upgraded to Intrepid last night) and Fedora 10. If you install the latest version of GE, 4.3, the problem goes away. However, the font rendering is kinda screwy. I managed to fix it on Fedora, but I forget what exactly I did.

4.3 works ok, but theirs no globe, starting it in root gives me a globe but the program crashes.

---

### Post by prakashkashyap on 2009-05-12
I am getting the below error when I try to run google earth. I am new to ubuntu. and want to stay in linux, can anyone pls help me to overcome this problem. I want to run GE in ubuntu. surely there should be some way of doing this.
thanks In advance. help greatly appreciated.


[email]p@p-desktop:~/.google[/email]earth$ googleearth
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  /usr/lib/googleearth/googleearth-bin [0x8058399]
  [0xb7fb8420]
  ./libbase.so(_ZN5earth8SpinLock4lockEj+0x22) [0xb7f723fc]
  ./libbase.so(_ZN5earth9LockGuardC1ERNS_8SpinLockE+0x1f) [0xb7f5827f]
  ./libnet.so(_ZN5earth3net18CurlHttpConnection13removeRequestEPNS0_15CurlHttpRequestE+0x25) [0xb7af545b]
  ./libnet.so(_ZN5earth3net15CurlHttpRequest4stopEv+0x20) [0xb7af54aa]
  ./libnet.so(_ZN5earth3net15CurlHttpRequestD0Ev+0x25) [0xb7af54d7]
  ./libnet.so(_ZN5earth3net11HttpRequest5unrefEv+0x35) [0xb7aed701]
  ./libnet.so(_ZN5earth6RefPtrINS_3net11HttpRequestEED1Ev+0x1e) [0xb7ae49c2]
  ./libnet.so(_ZN5earth3net14NetworkRequestD0Ev+0x28) [0xb7ae5a70]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7f4d4fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7f741d5]
  ./libnet.so(_ZN5earth3net7FetcherD0Ev+0x42) [0xb7ae9332]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7f4d4fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7f741d5]
  ./libwmsbase.so(_ZN5earth6RefPtrINS_3net7FetcherEEaSEPS2_+0x27) [0xb7b49055]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll7Texture12ProcessWorkQEd+0xec) [0xb39098e6]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll7Texture8endFrameEd+0x1a) [0xb3917c60]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext8endFrameEv+0x148) [0xb3915a94]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0xb2) [0xb39179f8]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0xa1) [0xb38d1b51]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x24) [0xb62e67d0]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x14) [0xb62d360c]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xb7f4d9bb]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xb6dc1fc2]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6d569a1]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xb6d574af]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xb6d4a43d]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xb6cfc24b]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEji+0x5a) [0xb6d705ea]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEi+0x2c) [0xb6d5633c]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEv+0x26) [0xb6d56376]
  /usr/lib/googleearth/liblayer.so(_ZN5earth5layer11LayerWindow12onFirstEarthERKNS_4evll11UpdateEventE+0x8e) [0xb0a8e1ea]
  /usr/lib/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE8doNotifyEMS2_FvRKS3_ES8_+0xa7) [0xb38daed3]
  /usr/lib/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE6notifyEMS2_FvRKS3_ES8_b+0x3e) [0xb38daf58]
  /usr/lib/googleearth/libevll.so [0xb38d431a]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xb7f4d9bb]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xb6dc1fc2]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6d569a1]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xb6d574af]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xb6d4a43d]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xb6cfc24b]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0xa9) [0xb6d704e9]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26) [0xb6d703e6]
  /usr/lib/googleearth/libqt-mt.so.3(_ZN12QApplication4execEv+0x1f) [0xb6d5639f]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEv+0x24f) [0xb76f5821]
  /usr/lib/googleearth/googleearth-bin(main+0x11f) [0x8058817]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb6091450]
  /usr/lib/googleearth/googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/p/.googleearth/crashlogs/crashlog-F6A0878F.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

---

