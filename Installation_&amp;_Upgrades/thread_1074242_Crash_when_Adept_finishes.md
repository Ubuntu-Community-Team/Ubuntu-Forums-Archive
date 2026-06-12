---
title: "Crash when Adept finishes"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Jeconti on 2009-02-19
So I decided today after a year with GNOME that I'd try out KDE and see what all the fuss was about. I did a fresh install of Kubuntu this afternoon and start working on installing software this evening. Except that every time Adept finishes installing new packages, KDE Daemon crashes and generates the following for a bug report:

```
Application: KDE Daemon (kded4), signal SIGSEGV
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb61298d0 (LWP 9932)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb744a2a4 in QString::operator== () from /usr/lib/libQtCore.so.4
#7  0xb7c6e9ed in ?? () from /usr/lib/libkio.so.5
#8  0xb7c6ec9b in ?? () from /usr/lib/libkio.so.5
#9  0xb750da60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#10 0xb750e7e2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#11 0xb7548633 in QSocketNotifier::activated () from /usr/lib/libQtCore.so.4
#12 0xb7513637 in QSocketNotifier::event () from /usr/lib/libQtCore.so.4
#13 0xb6a8b8ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#14 0xb6a9376e in QApplication::notify () from /usr/lib/libQtGui.so.4
#15 0xb79c772d in KApplication::notify () from /usr/lib/libkdeui.so.5
#16 0xb74f8e61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#17 0xb752370a in ?? () from /usr/lib/libQtCore.so.4
#18 0xb64ba6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#19 0xb64bdda3 in ?? () from /usr/lib/libglib-2.0.so.0
#20 0xb64bdf61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#21 0xb7523478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#22 0xb6b25ee5 in ?? () from /usr/lib/libQtGui.so.4
#23 0xb74f752a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#24 0xb74f76ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#25 0xb74f9da5 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#26 0xb6a8b767 in QApplication::exec () from /usr/lib/libQtGui.so.4
#27 0xb7f4a0a6 in kdemain () from /usr/lib/libkdeinit4_kded4.so
#28 0x080485a2 in _start ()
#0  0xb7f7c430 in __kernel_vsyscall ()

```

So far things are looking good for KDE, and reason this is happening on a Fresh Install? It happened again before, when I tried to download and enable proprietary drivers for my graphics card. That time it sent a signal 6. This one was signal 11. I have no idea what that means.

Any ideas?

---

### Post by yther on 2009-02-19
Adept is incorrectly named, in my opinion.  It should be called **In**ept.  Stuff like that happens to me all the time while using it, so I use **Synaptic** or **aptitude** instead.  Seriously, why Adept should either crash or decide to remove 95% of my KDE apps, while Synaptic does things properly, I can't understand.  :(

Sorry I can't help with your trouble, except to recommend that you just don't use that tool if it can't handle the stress.  Of course, you could also file some bug reports against Adept, and maybe one day it will be fixed.  Speaking honestly, though, I know it's bad but I'm usually too lazy or rushed to actually do that.

Oh yes, to add some useful info to my rant, "Signal 11" is known as a "segmentation fault," and here [is a nice explanation of the others]("http://developer.spikesource.com/wiki/index.php/Errors:Signals").

---

