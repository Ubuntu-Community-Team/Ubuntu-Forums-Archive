---
title: "fatal error"
date: 2008-11-13
forum: General Help
---

### Post by rock4christ on 2008-11-13
I intalled kde-desktop onto my xubuntu system this morning. I accidentally hit ctrl-alt-f12, and it force rebooted. now I just get a blank space with a "a fatal error has occurred" message containing this: > Application: Plasma Workspace (plasma), signal SIGSEGV
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb55266c0 (LWP 5815)]
[New Thread 0xb388ab90 (LWP 5824)]
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
#6  0xb71ae394 in QGraphicsLinearLayout::setSpacing ()
   from /usr/lib/libQtGui.so.4
#7  0xb3986368 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#8  0xb3986410 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#9  0xb7d57585 in Plasma::Applet::flushPendingConstraintsEvents ()
   from /usr/lib/libplasma.so.2
#10 0xb7d57bc6 in Plasma::Applet::timerEvent () from /usr/lib/libplasma.so.2
#11 0xb767853f in QObject::event () from /usr/lib/libQtCore.so.4
#12 0xb71b13c7 in QGraphicsWidget::event () from /usr/lib/libQtGui.so.4
#13 0xb6bf18ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#14 0xb6bf976e in QApplication::notify () from /usr/lib/libQtGui.so.4
#15 0xb7b3772d in KApplication::notify () from /usr/lib/libkdeui.so.5
#16 0xb7668e61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#17 0xb7696d81 in ?? () from /usr/lib/libQtCore.so.4
#18 0xb7693520 in ?? () from /usr/lib/libQtCore.so.4
#19 0xb59b76f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#20 0xb59bada3 in ?? () from /usr/lib/libglib-2.0.so.0
#21 0xb59baf61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#22 0xb7693478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#23 0xb6c8bee5 in ?? () from /usr/lib/libQtGui.so.4
#24 0xb766752a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#25 0xb76676ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#26 0xb68a6cab in KIO::NetAccess::enter_loop () from /usr/lib/libkio.so.5
#27 0xb68a6eac in KIO::NetAccess::statInternal () from /usr/lib/libkio.so.5
#28 0xb68a7cbb in KIO::NetAccess::stat () from /usr/lib/libkio.so.5
#29 0xb68a7d3b in KIO::NetAccess::mostLocalUrl () from /usr/lib/libkio.so.5
#30 0xb38a7f1e in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#31 0xb38a86ff in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#32 0xb7d87737 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.2
#33 0xb7d88531 in Plasma::Corona::initializeLayout ()
   from /usr/lib/libplasma.so.2
#34 0xb7fed199 in ?? () from /usr/lib/libkdeinit4_plasma.so
#35 0xb7fee880 in ?? () from /usr/lib/libkdeinit4_plasma.so
#36 0xb7ff0a81 in ?? () from /usr/lib/libkdeinit4_plasma.so
#37 0xb7fe243a in kdemain () from /usr/lib/libkdeinit4_plasma.so
#38 0x080485b2 in _start ()
#0  0xb802e430 in __kernel_vsyscall ()



is there a fix?

---

