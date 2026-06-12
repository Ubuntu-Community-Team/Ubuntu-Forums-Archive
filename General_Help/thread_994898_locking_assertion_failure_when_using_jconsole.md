---
title: "locking assertion failure when using jconsole"
date: 2008-11-27
forum: General Help
---

### Post by salma_nairi on 2008-11-27
Hello,

when using jconsole or opening jnpl file with java web start , i have this back trace log

Trace log:

locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7d8a767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7d8a8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb54ce1bd]
#3 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so [0xb55c722e]
#4 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so [0xb55a5ed7]
#5 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so [0xb55a6188]
#6 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xb55a648f]
#7 [0xb5d1a68e]
#8 [0xb5d12e9d]
#9 [0xb5d12e9d]
#10 [0xb5d10207]
#11 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so [0x620967d]
#12 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so [0x63057d8]
#13 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so [0x6209510]
#14 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f38b]
#15 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d2b96d]
#16 [0xb5d1a68e]
#17 [0xb5d12d37]
#18 [0xb5d10207]
#19 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so [0x620967d]
Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7d8a767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7d8a81e]
#2 /usr/lib/libX11.so.6 [0xb54cd518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb54c40a6]
#4 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so [0xb55a5189]
#5 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so [0xb55a53d5]
#6 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so [0xb55a6239]
#7 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xb55a648f]
#8 [0xb5d1a68e]
#9 [0xb5d12e9d]
#10 [0xb5d12e9d]
#11 [0xb5d10207]
#12 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so [0x620967d]
#13 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so [0x63057d8]
#14 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so [0x6209510]
#15 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f38b]
#16 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d2b96d]
#17 [0xb5d1a68e]
#18 [0xb5d12d37]
#19 [0xb5d10207]

my distribution is ubuntu 8.04 TLS and i tried the flowing instruction that i found on several forum but ther didn't solve my problem
sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so
sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so
export LIBXCB_ALLOW_SLOPPY_LOCK=true or
export LIBXCB_ALLOW_SLOPPY_LOCK=1

so i don't really know the cause of this error (it's a bug from jre or ubuntu distrib ) and i add that i installed sun-java6-jre on unbuntu 7.04 and used the same command ( jconsole or javaws ) i havn't this problem

If someone have an idea or issue it'll be helpful  :confused:

Best Regards

Nairi Salma
Software Engineer

---

