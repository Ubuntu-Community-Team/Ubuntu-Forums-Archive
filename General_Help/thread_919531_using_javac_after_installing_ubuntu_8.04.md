---
title: "using javac after installing ubuntu 8.04"
date: 2008-09-14
forum: General Help
---

### Post by hazooom on 2008-09-14
Hi, I just installed ubuntu 8.04, and was trying to compile some java code, but I somehow lost the javac settings. So I reinstalled java5 using
sudo apt-get install sun-java5-jdk
so javac is working again, however I get some "locking assertion failure", here is an example:

#0 /usr/lib/libxcb-xlib.so.0 [0xb177b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb177b8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb17c01bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb18b1dce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb189bd77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb189bef3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb189c136]
#7 [0xb2625bfa]
#8 [0xb261fb3b]
#9 [0xb261fb3b]
#10 [0xb261d219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77d42bc]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78e8ed8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77d40ef]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7831b9d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75d130d]
#16 [0xb26254ab]
#17 [0xb261fa64]
#18 [0xb261d219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77d42bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb177b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb177b81e]
#2 /usr/lib/libX11.so.6 [0xb17bf518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb17b60a6]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb189b0b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb189b303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb189bfa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb189c136]
#8 [0xb2625bfa]
#9 [0xb261fb3b]
#10 [0xb261fb3b]
#11 [0xb261d219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77d42bc]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78e8ed8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb77d40ef]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7831b9d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75d130d]
#17 [0xb26254ab]
#18 [0xb261fa64]
#19 [0xb261d219]



Anyone knows how this can be fixed??
Thank you.

---

### Post by ju2wheels on 2008-09-14
This is a common problem with libxcb which typically shows up with java apps.

Open a terminal and running the following should fix it:
```

export LIBXCB_ALLOW_SLOPPY_LOCK=1

```

You can also google "java libxcb lock assertion" for more threads on the issue.

---

