---
title: "KNotify crashing"
date: 2008-11-02
forum: General Help
---

### Post by Dragonslicer on 2008-11-02
Whenever knotify tries to do anything (message from Kopete, beep in Konsole, etc.), it crashes with a SIGABRT. It looks like the problem is with phonon. It might be this bug: [http://bugs.kde.org/show_bug.cgi?id=158088](http://bugs.kde.org/show_bug.cgi?id=158088). This was happening in 8.04 as well, but only after upgrading to KDE 4.1.2 (it worked fine in 4.1.0). Anyone know of any ways to work around this?


```
Application: KNotify (knotify4), signal SIGABRT
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
[New Thread 0xb66d7920 (LWP 8196)]
[New Thread 0xb3e26b90 (LWP 8606)]
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
#6  0xb808c430 in __kernel_vsyscall ()
#7  0xb6cd0880 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6cd2248 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7c60795 in qt_message_output () from /usr/lib/libQtCore.so.4
#10 0xb7c60872 in qFatal () from /usr/lib/libQtCore.so.4
#11 0xb7c60915 in qt_assert () from /usr/lib/libQtCore.so.4
#12 0xb4e72b60 in ?? () from /usr/lib/libkaudiodevicelist.so.4
#13 0xb4e73228 in Phonon::AudioDevice::AudioDevice ()
   from /usr/lib/libkaudiodevicelist.so.4
#14 0xb4e7c2c0 in ?? () from /usr/lib/libkaudiodevicelist.so.4
#15 0xb4e7ce24 in ?? () from /usr/lib/libkaudiodevicelist.so.4
#16 0xb4e7d17b in Phonon::AudioDeviceEnumerator::self ()
   from /usr/lib/libkaudiodevicelist.so.4
#17 0xb510d7f7 in ?? () from /usr/lib/kde4/plugins/phonon_platform/kde.so
#18 0xb51076fe in ?? () from /usr/lib/kde4/plugins/phonon_platform/kde.so
#19 0xb51077ff in ?? () from /usr/lib/kde4/plugins/phonon_platform/kde.so
#20 0xb6f1b1bc in ?? () from /usr/lib/libphonon.so.4
#21 0xb6f1b66e in ?? () from /usr/lib/libphonon.so.4
#22 0xb6f15e41 in ?? () from /usr/lib/libphonon.so.4
#23 0xb6f16b06 in Phonon::AudioOutput::AudioOutput ()
   from /usr/lib/libphonon.so.4
#24 0x080533fc in _start ()
#0  0xb808c430 in __kernel_vsyscall ()

```

---

### Post by Dragonslicer on 2008-11-06
-bump-

Upgraded to KDE 4.1.3 today, still have the same problem.

---

