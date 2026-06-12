---
title: "Google Earth won't run, maybe I installed it incorrectly?"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by InsomniacAgent on 2009-09-05
Google Earth will run for a few seconds, then it tries to load myplaces.kml and the application closes.

Anybody have any idea what I could do?

I installed it through the medibuntu repositories, I believe.

---

### Post by Partyboi2 on 2009-09-05
Open a terminal (Applications>Accessories>Terminal) and try starting it from their
```
googleearth 
```
Then post the output from the terminal, this will hopefully provide some further information on what is happening.

---

### Post by jacksaff on 2009-09-05
You could be trying to load a corrupt myplaces file (though I would expect GE to handle it more gracefully).

Try renaming the hidden file .googleearth in your home directory. GE will then start as if it was a totally new install so if it runs then we've narrowed the problem and we can look at the next step...

---

### Post by InsomniacAgent on 2009-09-06
Here's what it returned.

```
ryan@ryan-laptop:~$ googleearth
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  /usr/lib32/googleearth/googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  /usr/lib32/googleearth/googleearth-bin [0x8058399]
  [0xf7f4b400]
  ./libbase.so(_ZN5earth8SpinLock4lockEj+0x22) [0xf7f053fc]
  ./libbase.so(_ZN5earth9LockGuardC1ERNS_8SpinLockE+0x1f) [0xf7eeb27f]
  ./libnet.so(_ZN5earth3net18CurlHttpConnection13removeRequestEPNS0_15CurlHttpRequestE+0x25) [0xf7a8745b]
  ./libnet.so(_ZN5earth3net15CurlHttpRequest4stopEv+0x20) [0xf7a874aa]
  ./libnet.so(_ZN5earth3net15CurlHttpRequestD0Ev+0x25) [0xf7a874d7]
  ./libnet.so(_ZN5earth3net11HttpRequest5unrefEv+0x35) [0xf7a7f701]
  ./libnet.so(_ZN5earth6RefPtrINS_3net11HttpRequestEED1Ev+0x1e) [0xf7a769c2]
  ./libnet.so(_ZN5earth3net14NetworkRequestD0Ev+0x28) [0xf7a77a70]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xf7ee04fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xf7f071d5]
  ./libnet.so(_ZN5earth3net7FetcherD0Ev+0x42) [0xf7a7b332]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xf7ee04fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xf7f071d5]
  ./libwmsbase.so(_ZN5earth6RefPtrINS_3net7FetcherEEaSEPS2_+0x27) [0xf7adc055]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll18NetworkLinkFetcher9fetchDoneEv+0x890) [0xf2667486]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll18NetworkLinkFetcher12ProcessWorkQEd+0x38) [0xf266756a]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll18GeobaseContextImpl8endFrameEd+0x1a) [0xf266760c]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll13VisualContext8endFrameEv+0x19b) [0xf2764ae7]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0xb2) [0xf27669f8]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0xa1) [0xf2720b51]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x24) [0xf62787d0]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x14) [0xf626560c]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xf7ee09bb]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xf6d54fc2]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xf6ce99a1]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xf6cea4af]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xf6cdd43d]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xf6c8f24b]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEji+0x5a) [0xf6d035ea]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEi+0x2c) [0xf6ce933c]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEv+0x26) [0xf6ce9376]
  /usr/lib32/googleearth/liblayer.so(_ZN5earth5layer11LayerWindow12onFirstEarthERKNS_4evll11UpdateEventE+0x8e) [0xef4dd1ea]
  /usr/lib32/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE8doNotifyEMS2_FvRKS3_ES8_+0xa7) [0xf2729ed3]
  /usr/lib32/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE6notifyEMS2_FvRKS3_ES8_b+0x3e) [0xf2729f58]
  /usr/lib32/googleearth/libevll.so [0xf272331a]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xf7ee09bb]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xf6d54fc2]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xf6ce99a1]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xf6cea4af]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xf6cdd43d]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xf6c8f24b]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0xa9) [0xf6d034e9]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26) [0xf6d033e6]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication4execEv+0x1f) [0xf6ce939f]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEv+0x24f) [0xf7688821]
  /usr/lib32/googleearth/googleearth-bin(main+0x11f) [0x8058817]
  /lib32/libc.so.6(__libc_start_main+0xe5) [0xf6004775]
  /usr/lib32/googleearth/googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/ryan/.googleearth/crashlogs/crashlog-16979F9A.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.


```

---

### Post by InsomniacAgent on 2009-09-06
jacksaff, it's a fresh install.  I installed it, and then tried to run it, and got that message.

---

