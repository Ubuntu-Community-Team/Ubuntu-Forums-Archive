---
title: "[SOLVED] FrostWire not working after update"
date: 2008-08-28
forum: General Help
---

### Post by kahlil88 on 2008-08-28
I updated to FrostWire 4.17 and now when I open it, it's just a blank unresponsive window.

---

### Post by Crafty Kisses on 2008-08-28
Try running Frostwire in the Terminal, do you get any errors?

---

### Post by kahlil88 on 2008-08-28
Here's the terminal output:
```
HOSTNAME IS kahlil-desktop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_15]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./tritonus.jar:./mp3spi.jar:./guice-1.0.jar:./daap.jar:./messages.jar:./foxtrot.jar:./jmdns.jar:./aopalliance.jar:./jogg.jar:./jdic_stub.jar:./httpcore-4.0-beta2.jar:./jorbis.jar:./httpcore-nio-4.0-beta2.jar:./jcraft.jar:./onion-common.jar:./fw-irc.jar:./jdic.jar:./log4j.jar:./commons-logging.jar:./forms.jar:./themes.jar:./httpcore-niossl-4.0-alpha7.jar:./gettext-commons.jar:./looks.jar:./FrostWire.jar:./jl.jar:./lw-all.jar:./ProgressTabs.jar:./jaudiotagger.jar:./commons-codec-1.3.jar:./jflac.jar:./onion-fec.jar:./httpclient-4.0-alpha3.jar:./vorbisspi.jar:./clink.jar:./icu4j.jar
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7f9c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7f9c8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb06f31bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb07e3dce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb07cdd77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb07cdef3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb07ce136]
#7 [0xb264bc1b]
#8 [0xb2645b3b]
#9 [0xb2645b3b]
#10 [0xb2643219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78032bc]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb7917ed8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78030ef]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7860b9d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75f730d]
#16 [0xb264b4bb]
#17 [0xb2645a64]
#18 [0xb2643219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78032bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7f9c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7f9c81e]
#2 /usr/lib/libX11.so.6 [0xb06f2518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb06e90a6]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb07cd0b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb07cd303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb07cdfa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb07ce136]
#8 [0xb264bc1b]
#9 [0xb2645b3b]
#10 [0xb2645b3b]
#11 [0xb2643219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78032bc]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb7917ed8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78030ef]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7860b9d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75f730d]
#17 [0xb264b4bb]
#18 [0xb2645a64]
#19 [0xb2643219]
**FTA DEBUG: FOUND VALUE is: 124
Local key is: [B@acdd02
SimppSettingsManager.activateSimppSettings() - activating new settings
SimppSettingsManager.activateSimppSettings() - activating new settings
Trying to start chat panel...
initializing chat community...
Creating new IRC App...
Initializing new IRC App...
Smileys should be ACTIVE!
Initialized! new IRC App...
getting nick: kahlil88Chat enabled?: true
Removing previous banners...
Getting banners from server...
Loading banners...
User-Agent: FrostWire/Linux/4.17.0
Initializing Connection Doctor...
FrostWire's connection doctor will be started at 4 seconds, now waiting: 1 seconds
FrostWire's connection doctor will be started at 4 seconds, now waiting: 2 seconds
SponsorLoader.startElement -> Detected a custom refreshrate -> 0
SponsorLoader.startElement -> Killing Banner Refresh Tasks
BannerContainer.setupBannerRefreshTask() - No banner refresh for me.
Connection Doctor timer is now ended. Interrupted?true
Fetching ip address on separate thread
My IP address looks like this ->4.182.210.236
MY IP ADDRESS IS THIS ->>>> 4.182.210.236
```

---

### Post by todak on 2008-08-28
Try upgrading your java to 1.6 and it should work.

---

### Post by forger on 2008-08-28
yep, 1.6 should do it:
```
sudo apt-get install sun-java6-jre sun-java6-bin
```

---

### Post by kahlil88 on 2008-08-28
Thanks! Updating Java fixed it right up.

---

