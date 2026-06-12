---
title: "How to install debug package for plasma_applet_bubblemon"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by grahamt2280 on 2009-07-05
Hi All,

I'm using Kubuntu Jaunty with KDE 4.3 RC1 from the PPA as per this link:
[http://www.kubuntu.org/news/kde-4.2.95](http://www.kubuntu.org/news/kde-4.2.95)

It frequently crashes, and I lose my desktop. Alt-F2 still works, so I can launch any program I want and keep working.

I get the Crash Reporting Assistant [CRA] pop up when the crash happens and I can run a backtrace.

I've posted the full back trace below, but the CRA says the backtrace is "probably not useful" because of the double questionmarks "??" in this line:

#6  0xa949dbe6 in ?? () from /usr/lib/kde4/plasma_applet_bubblemon.so

The CRA indicates that I should follow the guidance on this page:

[http://techbase.kde.org/Development/Tutorials/Debugging/How_to_create_useful_crash_reports#Preparing_your_KDE_packages](http://techbase.kde.org/Development/Tutorials/Debugging/How_to_create_useful_crash_reports#Preparing_your_KDE_packages)

That section of that page relevant to Kubuntu indicates that I should install the debug package for plasma_applet_bubblemon, which it indicates should be named as:

plasma_applet_bubblemon-dbg

But no such debug package is available.

An apt-cache search for that package returns nothing :- neither the debug package, nor the normal package without the -dbg suffix.

root@NX9420# apt-cache search plasma_applet_bubblemon
root@NX9420#

Does anyone have any pointers for me how I might go about installing plasma_applet_bubblemon-dbg? 

I'd really quite like to be able to file a useful bug report...

Thanks in advance.

--------------------------------------------------
Backtrace appears below
--------------------------------------------------

Application: Plasma Workspace (kdeinit4), signal: Floating point exception
[Current thread is 0 (LWP 4665)]

Thread 2 (Thread 0xa91aab90 (LWP 4668)):
#0  0xb8090430 in __kernel_vsyscall ()
#1  0xb65560e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb67362ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e899b2 in QWaitCondition::wait (this=0x938d5e8, mutex=0x938d5e4, time=4294967295) at thread/qwaitcondition_unix.cpp:87
#4  0xb77c5152 in QHostInfoAgent::run (this=0x938d5d8) at kernel/qhostinfo.cpp:260
#5  0xb7e8896e in QThreadPrivate::start (arg=0x938d5d8) at thread/qthread_unix.cpp:189
#6  0xb65524ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb672749e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb6060a10 (LWP 4665)):
[KCrash Handler]
#6  0xa949dbe6 in ?? () from /usr/lib/kde4/plasma_applet_bubblemon.so
#7  0xa949d4e3 in ?? () from /usr/lib/kde4/plasma_applet_bubblemon.so
#8  0xb7f92ca8 in QMetaObject::activate (sender=0x9533400, from_signal_index=4, to_signal_index=4, argv=0x0) at kernel/qobject.cpp:3069
#9  0xb7f93932 in QMetaObject::activate (sender=0x9533400, m=0xb806f904, local_signal_index=0, argv=0x0) at kernel/qobject.cpp:3143
#10 0xb7fce717 in QTimer::timeout (this=0x9533400) at .moc/release-shared/moc_qtimer.cpp:128
#11 0xb7f986fe in QTimer::timerEvent (this=0x9533400, e=0xbfbad4cc) at kernel/qtimer.cpp:261
#12 0xb7f8d15f in QObject::event (this=0x9533400, e=0xbfbad4cc) at kernel/qobject.cpp:1082
#13 0xb6a0ce9c in QApplicationPrivate::notify_helper (this=0x8d60618, receiver=0x9533400, e=0xbfbad4cc) at kernel/qapplication.cpp:4084
#14 0xb6a1519e in QApplication::notify (this=0x8d5a7e8, receiver=0x9533400, e=0xbfbad4cc) at kernel/qapplication.cpp:3631
#15 0xb75473dd in KApplication::notify (this=0x8d5a7e8, receiver=0x9533400, event=0xbfbad4cc) at /build/buildd/kde4libs-4.2.95/kdeui/kernel/kapplication.cpp:302
#16 0xb7f7ca3b in QCoreApplication::notifyInternal (this=0x8d5a7e8, receiver=0x9533400, event=0xbfbad4cc) at kernel/qcoreapplication.cpp:602
#17 0xb7fabd71 in QTimerInfoList::activateTimers (this=0x8d63334) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:213
#18 0xb7fa84e0 in timerSourceDispatch (source=0x8d63300) at kernel/qeventdispatcher_glib.cpp:164
#19 0xb659fb88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#20 0xb65a30eb in ?? () from /usr/lib/libglib-2.0.so.0
#21 0xb65a3268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#22 0xb7fa8438 in QEventDispatcherGlib::processEvents (this=0x8d5dec0, flags={i = -1078274488}) at kernel/qeventdispatcher_glib.cpp:323
#23 0xb6aae365 in QGuiEventDispatcherGlib::processEvents (this=0x8d5dec0, flags={i = -1078274440}) at kernel/qguieventdispatcher_glib.cpp:202
#24 0xb7f7b06a in QEventLoop::processEvents (this=0xbfbad6f0, flags={i = -1078274376}) at kernel/qeventloop.cpp:149
#25 0xb7f7b4aa in QEventLoop::exec (this=0xbfbad6f0, flags={i = -1078274312}) at kernel/qeventloop.cpp:200
#26 0xb7f7d959 in QCoreApplication::exec () at kernel/qcoreapplication.cpp:880
#27 0xb6a0cd17 in QApplication::exec () at kernel/qapplication.cpp:3553
#28 0xb4aa9510 in kdemain () from /usr/lib/libkdeinit4_plasma-desktop.so
#29 0x0804e1c0 in launch (argc=1, _name=0x8d27c5c "/usr/bin/plasma-desktop", args=0x8d27c74 "", cwd=0x0, envc=0, envs=0x8d27c78 "", reset_env=false, tty=0x0, avoid_loops=false, 
    startup_id_str=0x80512d1 "0") at /build/buildd/kde4libs-4.2.95/kinit/kinit.cpp:672
#30 0x0804e99d in handle_launcher_request (sock=7, who=<value optimized out>) at /build/buildd/kde4libs-4.2.95/kinit/kinit.cpp:1164
#31 0x0804ef25 in handle_requests (waitForPid=0) at /build/buildd/kde4libs-4.2.95/kinit/kinit.cpp:1357
#32 0x0804fb0a in main (argc=2, argv=0xbfbadee4, envp=0xbfbadef0) at /build/buildd/kde4libs-4.2.95/kinit/kinit.cpp:1784

---

