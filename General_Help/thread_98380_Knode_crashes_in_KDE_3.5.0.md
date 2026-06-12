---
title: "Knode crashes in KDE 3.5.0"
date: 2005-12-03
forum: General Help
---

### Post by bertilow on 2005-12-03
I upgraded my Kubuntu to KDE 3.5.0. Most things work well, except for Knode. Now it just crashes on start. What to do? Any ideas?

OK. Here's the backtrace:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
[REPEAT A LOT]
[Thread debugging using libthread_db enabled]
[New Thread -1242929472 (LWP 10125)]
(no debugging symbols found)
[REPEAT A LOT]
[KCrash handler]
#4  0xb70c1949 in QTimer::stop () from /usr/lib/libqt-mt.so.3
#5  0xb7ed708d in KNode::ArticleWidget::readConfig ()
   from /usr/lib/libknodecommon.so
#6  0xb7f13a88 in KNode::ArticleWidget::ArticleWidget ()
   from /usr/lib/libknodecommon.so
#7  0xb7f1be76 in KNMainWidget::KNMainWidget ()
   from /usr/lib/libknodecommon.so
#8  0x0804ee3e in ?? ()
#9  0x081f81f8 in ?? ()
#10 0x0805f510 in ?? ()
#11 0x00000001 in ?? ()
#12 0x0805f450 in ?? ()
#13 0x00000000 in ?? ()
#14 0x00000001 in ?? ()
#15 0x000000cc in ?? ()
#16 0xb7df1cd0 in ?? () from /usr/lib/libstdc++.so.6
#17 0x000000cc in ?? ()
#18 0xb7a63284 in KUniqueApplication::metaObj () from /usr/lib/libkdecore.so.4
#19 0xbf97d288 in ?? ()
#20 0xb7dcd4c5 in operator new () from /usr/lib/libstdc++.so.6
#21 0x0804f579 in ?? ()
#22 0x0805f450 in ?? ()
#23 0x00000000 in ?? ()
#24 0xffffffff in ?? ()
#25 0x00000000 in ?? ()
#26 0xbf97d364 in ?? ()
#27 0x080604c0 in ?? ()
#28 0x00001093 in ?? ()
#29 0xb7940d7e in KApplication::setStartupId () from /usr/lib/libkdecore.so.4
#30 0xb79ca894 in KUniqueApplication::processDelayed ()
   from /usr/lib/libkdecore.so.4
#31 0xb79cc1d9 in KUniqueApplication::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#32 0x0804e917 in ?? ()
#33 0xbf97da54 in ?? ()
#34 0x00000012 in ?? ()
#35 0xbf97d458 in ?? ()
#36 0xb709dbef in QPtrList<QConnection>::first () from /usr/lib/libqt-mt.so.3
#37 0xb709c929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#38 0xb73fbe92 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#39 0xb70ba344 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#40 0xb70c1e88 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#41 0xb7033f80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#42 0xb7034172 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#43 0xb79b8c3c in KApplication::notify () from /usr/lib/libkdecore.so.4
#44 0xb6fc4db7 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#45 0xb702599b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#46 0xb6fd8a84 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#47 0xb704bcfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#48 0xb704bc1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#49 0xb7032c13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#50 0x0804eb59 in ?? ()
#51 0xbf97da54 in ?? ()
#52 0xbf97db68 in ?? ()
#53 0x00000001 in ?? ()
#54 0x00000000 in ?? ()
#55 0xb7c1f391 in malloc () from /lib/tls/i686/cmov/libc.so.6
#56 0xb7bceea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#57 0x0804e4e1 in ?? ()

---

### Post by asimon on 2005-12-03
[QUOTE=bertilow]
#5  0xb7ed708d in KNode::ArticleWidget::readConfig ()
   from /usr/lib/libknodecommon.so
[/QUOTE]
Looks like it crashes while reading it's configuration. Maybe there's something fishy in the config file. You could try to remove the config file (of course in this case you loose your knode configuration) and try if it still crashes.
I.e. exit knode and from a terminal window do something like
```

$ mv ~/.kde/share/config/knoderc /tmp

```
to move the knode config away. Then try knode again. If it doesn't help you can move your old config file to it's right place again, i.e.
```

$ mv /tmp/knoderc ~/.kde/share/config/

```

---

### Post by bertilow on 2005-12-03
[QUOTE=asimon]Looks like it crashes while reading it's configuration.[/QUOTE]

Yes. That was it. I removed the config file, and let Knode make a new one. Now all is fine. No real data lost. Thanks a lot!

---

### Post by bertilow on 2005-12-04
I wrote:

[QUOTE=bertilow]Yes. That was it. I removed the config file, and let Knode make a new one. Now all is fine. No real data lost. Thanks a lot![/QUOTE]

But I spoke too soon. Now it crashes again at start. So I guess it's back to Thunderbird.

Here's the new backtrace (seems to be slightly different) in case anyone is interested:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
[REPEAT A LOT]
[Thread debugging using libthread_db enabled]
[New Thread -1242970432 (LWP 7321)]
(no debugging symbols found)
[REPEAT A LOT]
[KCrash handler]
#4  0xb70b7949 in QTimer::stop () from /usr/lib/libqt-mt.so.3
#5  0xb7ecd08d in KNode::ArticleWidget::readConfig ()
   from /usr/lib/libknodecommon.so
#6  0xb7f09a88 in KNode::ArticleWidget::ArticleWidget ()
   from /usr/lib/libknodecommon.so
#7  0xb7f11e76 in KNMainWidget::KNMainWidget ()
   from /usr/lib/libknodecommon.so
#8  0x0804ee3e in ?? ()
#9  0x081f8548 in ?? ()
#10 0x0805f4e0 in ?? ()
#11 0x00000001 in ?? ()
#12 0x0805f420 in ?? ()
#13 0x00000000 in ?? ()
#14 0x00000001 in ?? ()
#15 0x000000cc in ?? ()
#16 0xb7de7cd0 in ?? () from /usr/lib/libstdc++.so.6
#17 0x000000cc in ?? ()
#18 0xb7a59284 in KUniqueApplication::metaObj () from /usr/lib/libkdecore.so.4
#19 0xbfb74f78 in ?? ()
#20 0xb7dc34c5 in operator new () from /usr/lib/libstdc++.so.6
#21 0x0804f579 in ?? ()
#22 0x0805f420 in ?? ()
#23 0x00000000 in ?? ()
#24 0xbfb74fa8 in ?? ()
#25 0xb738432b in QGArray::~QGArray () from /usr/lib/libqt-mt.so.3
#26 0xb79c0894 in KUniqueApplication::processDelayed ()
   from /usr/lib/libkdecore.so.4
#27 0xb79c21d9 in KUniqueApplication::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#28 0x0804e917 in ?? ()
#29 0xbfb75744 in ?? ()
#30 0x00000012 in ?? ()
#31 0xbfb75148 in ?? ()
#32 0xb7093bef in QPtrList<QConnection>::first () from /usr/lib/libqt-mt.so.3
#33 0xb7092929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#34 0xb73f1e92 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#35 0xb70b0344 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#36 0xb70b7e88 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#37 0xb7029f80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#38 0xb702a172 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#39 0xb79aec3c in KApplication::notify () from /usr/lib/libkdecore.so.4
#40 0xb6fbadb7 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#41 0xb701b99b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#42 0xb6fcea84 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#43 0xb7041cfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#44 0xb7041c1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#45 0xb7028c13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#46 0x0804eb59 in ?? ()
#47 0xbfb75744 in ?? ()
#48 0xbfb75858 in ?? ()
#49 0x00000001 in ?? ()
#50 0x00000000 in ?? ()
#51 0xb7c15391 in malloc () from /lib/tls/i686/cmov/libc.so.6
#52 0xb7bc4ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#53 0x0804e4e1 in ?? ()

---

