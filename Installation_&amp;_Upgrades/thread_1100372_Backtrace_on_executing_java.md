---
title: "Backtrace on executing java"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by GolanTrevize on 2009-03-19
hello together,

**Error**
since this morning I get a backtrace from each start of a java-application on a 8.04 installation

**Description**
At the moment, any java-application I start aside from eclipse, which runs obviously still without errors, throws the following backtrace:
```

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7399767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb73998b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x8b8521bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8c03bdce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8c025d77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8c025ef3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x8c026136]
#7 [0xb13b3008]
#8 [0xb13acb6b]
#9 [0xb13acb6b]
#10 [0xb13aa236]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7636eec]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7806ae8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7636d1f]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb769482d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb734930d]
#16 [0xb13b2898]
#17 [0xb13aca94]
#18 [0xb13aa236]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7636eec]

```The application then starts and seems to run without further errors.

**Environment**
This error occurrs on my Hardy 8.04 since this morning. I installed the following updates yesterday:

```

gstreamer0.10-plugins-good (0.10.7-3ubuntu0.1) to 0.10.7-3ubuntu0.2
libavcodec1d (3:0.cvs20070307-5ubuntu7.1) to 3:0.cvs20070307-5ubuntu7.3
libavformat1d (3:0.cvs20070307-5ubuntu7.1) to 3:0.cvs20070307-5ubuntu7.3
libavutil1d (3:0.cvs20070307-5ubuntu7.1) to 3:0.cvs20070307-5ubuntu7.3
libglib2.0-0 (2.16.6-0ubuntu1) to 2.16.6-0ubuntu1.1
libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) to 3.12.0.3-0ubuntu0.8.04.5
libpostproc1d (3:0.cvs20070307-5ubuntu7.1) to 3:0.cvs20070307-5ubuntu7.3

```The error appears with each java - swing / awt application. 
Examples:

[LIST]
[*]ldapbrowser (lbe)
[*]my own applications
[*]luke
[*]jmeter
[*]argouml
[*]jap
[/LIST]
i.e. virtually any java application suffers from this error.

I tried it with any JDK I have installed:

[LIST]
[*]sun-java5-jdk
[*]sun-java6-jdk
[*]jdk1.6.0_01 (jdk directly from sun)
[*]jdk1.5.0_14 (jdk directly from sun)
[/LIST]
I did not try 1.4 jdks, because my applications don't run on 1.4

[B]Question:
[/B]
[LIST]
[*]Why is this?
[*]Is there a workaround?
[*]Which update causes the errors?
[*]Most important: What can I do?
[*]Am I the only one experiencing this kind of problem?
[/LIST]
thanks in advance 
Golan

---

### Post by GolanTrevize on 2009-03-24
bump...

---

