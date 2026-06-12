---
title: "voice-stress analysis complilation"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by r4z0rw0lf on 2009-01-11
I am trying to compile a for voice stress analysis called liarliar. but every time I try to ./configure it says i need gstreamer, gtkmm and gthread
```

checking for gtkmm-2.0 gthread-2.0 gstreamer-0.6... Package gtkmm-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtkmm-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtkmm-2.0' found Package gstreamer-0.6 was not found in the pkg-config search path. Perhaps you should add the directory containing `gstreamer-0.6.pc' to the PKG_CONFIG_PATH environment variable No package 'gstreamer-0.6' found
configure: error: Library requirements (gtkmm-2.0 gthread-2.0 gstreamer-0.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
I have no idea on how to get these so could someon help?
here is the programs sourceforge:[http://liarliar.sourceforge.net/](http://liarliar.sourceforge.net/)

---

### Post by r4z0rw0lf on 2009-01-11
Bump

---

### Post by lloyd_b on 2009-01-11
You just need to install some packages:

In a terminal window:
```
sudo apt-get install libgtkmm-2.4-dev libglib2.0-dev libgstreamer0.10-dev
```
(or install these packages using a GUI package manager like Synaptic).
should install the missing dependencies (note that probably a number of other packages will be automagically installed, to satisfy dependencies).

Lloyd B.

---

### Post by r4z0rw0lf on 2009-01-11
I did what you said and it told me they were all up-to-date.

---

### Post by r4z0rw0lf on 2009-01-11
I really need help... I'm bumping my head on my desk right now...

---

### Post by r4z0rw0lf on 2009-01-13
I really need help, you know

---

### Post by Partyboi2 on 2009-01-14
Try compiling it using an older version of gstreamer as shown from this blog.

**Orginal**
[http://damnsmallblog.blogspot.com/2008/04/liarliar-open-source.html](http://damnsmallblog.blogspot.com/2008/04/liarliar-open-source.html)[B]

Translated
[/B][http://translate.google.com/translate?hl=en&ie=UTF-8&oe=UTF-8&langpair=ru|en&u=http://damnsmallblog.blogspot.com/2008/04/liarliar-open-source.html]("http://translate.google.com/translate?hl=en&ie=UTF-8&oe=UTF-8&langpair=ru%7Cen&u=http://damnsmallblog.blogspot.com/2008/04/liarliar-open-source.html")

---

### Post by r4z0rw0lf on 2009-01-15
i did this and make keeps spittng out an error like : ```
gstbasicscheduler.c: In function 'gst_basic_scheduler_reset':
gstbasicscheduler.c:1043: error: lvalue required as left operand of assignment

```

---

