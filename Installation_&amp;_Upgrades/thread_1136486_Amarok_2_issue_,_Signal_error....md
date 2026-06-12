---
title: "Amarok 2 issue , Signal error..."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by samuraitor on 2009-04-25
Hi guys, 

I am having some troubles with amarok 2. Whenever I try to open it , I get the signal error below, how to I go about fixing it ?



Application: Amarok (amarok), signal SIGSEGV
[Current thread is 0 (LWP 4500)]

Thread 9 (Thread 0xb0396b90 (LWP 4501)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb786b412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0f7eae3 in ?? () from /usr/lib/libxine.so.1

Thread 8 (Thread 0xafae5b90 (LWP 4502)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb6785ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb44b474b in g_poll () from /usr/lib/libglib-2.0.so.0
#3  0xb44a6f82 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb44a7268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#5  0xb6aaa457 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#6  0xb6a7d06a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#7  0xb6a7d4aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#8  0xb6987639 in QThread::exec () from /usr/lib/libQtCore.so.4
#9  0xb0fcc20a in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#10 0xb698a96e in ?? () from /usr/lib/libQtCore.so.4
#11 0xb78674ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb679049e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xab2dcb90 (LWP 4508)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb6785ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xafb14b19 in ?? () from /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 6 (Thread 0xaf2d7b90 (LWP 4509)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb786b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0f8fd8e in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 5 (Thread 0xaead6b90 (LWP 4514)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb786b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb698b9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5deb148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5dedeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5de9d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5dedfea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5deb6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5debfbe in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5dec5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#10 0xb698a96e in ?? () from /usr/lib/libQtCore.so.4
#11 0xb78674ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb679049e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xacfa3b90 (LWP 4515)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb786b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb698b9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5deb148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5dedeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5de9d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5dedfea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5deb6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5debfbe in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5dec5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#10 0xb698a96e in ?? () from /usr/lib/libQtCore.so.4
#11 0xb78674ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb679049e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xac7a2b90 (LWP 4517)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb786b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb698b9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5deb148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5dedeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5de9d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5dedfea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5deb6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5dee009 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5deb6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5dee009 in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5deb6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#12 0xb5debfbe in ?? () from /usr/lib/libthreadweaver.so.4
#13 0xb5dec5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#14 0xb698a96e in ?? () from /usr/lib/libQtCore.so.4
#15 0xb78674ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb679049e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xabdffb90 (LWP 4518)):
#0  0xb7fef430 in __kernel_vsyscall ()
#1  0xb786b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb698b9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5deb148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5dedeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5de9d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5dedfea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5deb6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5dee009 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5deb6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5debfbe in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5dec5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#12 0xb698a96e in ?? () from /usr/lib/libQtCore.so.4
#13 0xb78674ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb679049e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb3008950 (LWP 4500)):
[KCrash Handler]
#6  0xb4c3a733 in QFormInternal::domPropertyToVariant () from /usr/lib/libamarokplasma.so.2
#7  0xb4bdf437 in QFormInternal::QAbstractFormBuilder::toVariant () from /usr/lib/libamarokplasma.so.2
#8  0xb4bf8cfa in QFormInternal::QFormBuilder::applyProperties () from /usr/lib/libamarokplasma.so.2
#9  0xb4bd5efd in QFormInternal::FormBuilderPrivate::applyProperties () from /usr/lib/libamarokplasma.so.2
#10 0xb4be29eb in QFormInternal::QAbstractFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#11 0xb4bfa248 in QFormInternal::QFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#12 0xb4bd4353 in QFormInternal::FormBuilderPrivate::create () from /usr/lib/libamarokplasma.so.2
#13 0xb4be1704 in QFormInternal::QAbstractFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#14 0xb4bf8a8b in QFormInternal::QFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#15 0xb4bd4821 in QFormInternal::FormBuilderPrivate::create () from /usr/lib/libamarokplasma.so.2
#16 0x9c61eff6 in QFormInternal::QAbstractFormBuilder::load () from /usr/lib/kde4/plugins/script/libqtscript_uitools.so
#17 0x9c6055fa in QUiLoader::load () from /usr/lib/kde4/plugins/script/libqtscript_uitools.so
#18 0x9c60156c in ?? () from /usr/lib/kde4/plugins/script/libqtscript_uitools.so
#19 0xb5c0608b in ?? () from /usr/lib/libQtScript.so.4
#20 0xb5bcd832 in ?? () from /usr/lib/libQtScript.so.4
#21 0xb5bfd17b in ?? () from /usr/lib/libQtScript.so.4
#22 0xb5bf122b in ?? () from /usr/lib/libQtScript.so.4
#23 0xb5bde617 in QScriptEngine::evaluate () from /usr/lib/libQtScript.so.4
#24 0xb7b82c13 in ScriptManager::slotRunScript () from /usr/lib/libamaroklib.so.1
#25 0xb7b83a60 in ScriptManager::slotConfigChanged () from /usr/lib/libamaroklib.so.1
#26 0xb7b852d2 in ScriptManager::findScripts () from /usr/lib/libamaroklib.so.1
#27 0xb7b857a3 in ScriptManager::qt_metacall () from /usr/lib/libamaroklib.so.1
#28 0xb6a94ca8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#29 0xb6a95932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#30 0xb6a9a0a7 in ?? () from /usr/lib/libQtCore.so.4
#31 0xb6a9a1cc in ?? () from /usr/lib/libQtCore.so.4
#32 0xb6a8f15f in QObject::event () from /usr/lib/libQtCore.so.4
#33 0xb6f4ff2c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#34 0xb6f5822e in QApplication::notify () from /usr/lib/libQtGui.so.4
#35 0xb7e3c94d in KApplication::notify () from /usr/lib/libkdeui.so.5
#36 0xb6a7ea3b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#37 0xb6aadd71 in ?? () from /usr/lib/libQtCore.so.4
#38 0xb6aaa4e0 in ?? () from /usr/lib/libQtCore.so.4
#39 0xb44a3b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#40 0xb44a70eb in ?? () from /usr/lib/libglib-2.0.so.0
#41 0xb44a7268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#42 0xb6aaa438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#43 0xb6ff13f5 in ?? () from /usr/lib/libQtGui.so.4
#44 0xb6a7d06a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#45 0xb6a7d4aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#46 0xb6a7f959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#47 0xb6f4fda7 in QApplication::exec () from /usr/lib/libQtGui.so.4
#48 0x0814c4b2 in _start ()

---

