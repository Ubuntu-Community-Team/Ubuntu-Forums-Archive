---
title: "Java Locking assertion failure"
date: 2008-09-18
forum: General Help
---

### Post by murder2 on 2008-09-18
I get "Locking assertion failure" every time I run a Java program on my laptop. It doesn't seem to a problem, things still work the way they should, but I was wondering if somebody know more about why I get this error, and perhaps a way to fix it?

```

$ dev/testing/jakarta-jmeter-2.3.1/bin/jmeter
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f55861db97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f55861dba84]
#2 /usr/lib/libX11.so.6(_XReply+0x10f) [0x7f5586a34f4f]
#3 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so [0x7f5586f4c826]
#4 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so [0x7f5586f2f2ab]
#5 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so [0x7f5586f2f57d]
#6 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f5586f2f7f2]
#7 [0x7f559c1aa5e3]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f55861db97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f55861dba15]
#2 /usr/lib/libX11.so.6 [0x7f5586a34323]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2c) [0x7f5586a2b72c]
#4 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so [0x7f5586f2e645]
#5 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so [0x7f5586f2e899]
#6 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so [0x7f5586f2f61f]
#7 /home/jon/dev/jdk1.6.0_03/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f5586f2f7f2]
#8 [0x7f559c1aa5e3]

```

---

### Post by siman on 2008-09-26
i had the same problem with jmeter. i guess you are running a 64bit system?

try installing the 32bit java6 version (its in the repos) and use that to start jmeter. worked for me.

---

