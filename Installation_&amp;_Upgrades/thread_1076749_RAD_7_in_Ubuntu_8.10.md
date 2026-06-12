---
title: "RAD 7 in Ubuntu 8.10"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by dilkington on 2009-02-21
Hi there,

am trying to install RAD in ubuntu 8.10. I have followed the post [here]("http://alexcozzi.blogspot.com/2007/01/rational-application-developer-7-on.html")  and also [here]("http://rende.se/index.php?n=Main.UbuntuHardyOnT61") but hitting the following issue.

The installation of RAD7 starts up fine (launchpad) but after selecting the RAD7 product the installation manager window appears and is blank. When closing the window I get the following trace

```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x96c007c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0x96c00891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0x96050494]
#3 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/xawt/libmawt.so(XineramaQueryScreens+0x91) [0x96130a11]
#4 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/xawt/libmawt.so(xineramaInit+0x58) [0x9611abe8]
#5 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/xawt/libmawt.so(awt_init_Display+0xe1) [0x9611ad21]
#6 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libj9vm23.so [0xb7d8a189]
#7 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_J9VMInternals_initializeImpl+0x7e) [0xb77f987e]
#8 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_Class_forNameImpl+0x2be) [0xb7801de2]
#9 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_J9VMInternals_initializeImpl+0x7e) [0xb77f987e]
#10 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_Class_forNameImpl+0x2be) [0xb7801de2]
#11 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libj9vm23.so [0xb7db550c]
#12 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libj9prt23.so [0xb7d68c6a]
#13 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libj9vm23.so [0xb7db3e11]
#14 /tmp/istemp31862052223814/_bundledJRE_/jre/bin/libj9thr23.so [0xb7e28d93]
#15 /lib/tls/i686/cmov/libpthread.so.0 [0xb7fb150f]
#16 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7f107ee]
```


Anyone any ideas ?

thanks

---

### Post by dilkington on 2009-02-23
Managed to sort this. I found a related post which detailed AWT and the desktop effects interfering with the installation and presenting a blank screen with visual paradigm.

To get round this : ensure you do not have desktop visual effects enabled, and hey presto it all works fine and dandy :)

---

