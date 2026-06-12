---
title: "Open GL not working (drivers installed)."
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-09-30
I installed the ati drivers and they are working.

I cant open the opengl section in the info center (kubuntu)
I cant view open gl screen savers.
I CAN use billards-gl which uses open gl (i think) and it works.

roderick@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

tv-out works and 3d games also work..?
anyone know where i should start ?

---

### Post by floyd27 on 2005-09-30
..also
when i try to open the opengl in the kinfo center it just crashes and gives me the crash error. thats whay i mean by cant get ino it.

thnx

---

### Post by floyd27 on 2005-10-01
This is the backtrace toof the error i keep getting. Telling me that info center has crashed.
It only does it when i try to access the open gl tab, the rest work fine..












[Thread debugging using libthread_db enabled]
[New Thread -1235662304 (LWP 9380)]
[KCrash handler]
#4  0xb662d66b in strstr () from /lib/tls/i686/cmov/libc.so.6
#5  0xb61ba220 in KMemoryWidget::qt_static_property ()
   from /usr/lib/kde3/kcm_info.so
#6  0xb61bc5bc in KMemoryWidget::qt_static_property ()
   from /usr/lib/kde3/kcm_info.so
#7  0xb61bf470 in print_glx_glu () from /usr/lib/kde3/kcm_info.so
#8  0xb61bf998 in print_glx_glu () from /usr/lib/kde3/kcm_info.so
#9  0xb61bf9b1 in GetInfo_OpenGL () from /usr/lib/kde3/kcm_info.so
#10 0xb61ae208 in KInfoListWidget::load () from /usr/lib/kde3/kcm_info.so
#11 0xb61ae9b5 in KInfoListWidget::KInfoListWidget ()
   from /usr/lib/kde3/kcm_info.so
#12 0xb61b30b7 in create_opengl () from /usr/lib/kde3/kcm_info.so
#13 0xb7a529f1 in KCModuleLoader::load () from /usr/lib/libkutils.so.1
#14 0xb7a53407 in KCModuleLoader::loadModule () from /usr/lib/libkutils.so.1
#15 0xb7a52ec2 in KCModuleLoader::loadModule () from /usr/lib/libkutils.so.1
#16 0xb7fc3973 in ConfigModule::module () from /usr/lib/libkdeinit_kcontrol.so
#17 0xb7fba326 in ModuleWidget::load () from /usr/lib/libkdeinit_kcontrol.so
#18 0xb7fba9e8 in DockContainer::loadModule ()
   from /usr/lib/libkdeinit_kcontrol.so
#19 0xb7fbac95 in DockContainer::dockModule ()
   from /usr/lib/libkdeinit_kcontrol.so
#20 0xb7fb7ab5 in TopLevel::activateModule ()
   from /usr/lib/libkdeinit_kcontrol.so
#21 0xb7fb451a in TopLevel::qt_invoke () from /usr/lib/libkdeinit_kcontrol.so
#22 0xb6c97067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb7fbb31a in AboutWidget::moduleSelected ()
   from /usr/lib/libkdeinit_kcontrol.so
#24 0xb7fbde50 in AboutWidget::slotModuleLinkClicked ()
   from /usr/lib/libkdeinit_kcontrol.so
#25 0xb7fbb3a5 in AboutWidget::qt_invoke ()
   from /usr/lib/libkdeinit_kcontrol.so
#26 0xb6c96fdd in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0xb7ab16b5 in KParts::BrowserExtension::openURLRequest ()
   from /usr/lib/libkparts.so.2
#28 0xb7d243dd in KHTMLPart::urlSelected () from /usr/lib/libkhtml.so.4
#29 0xb7d8f9b1 in DOM::removeForbidden () from /usr/lib/libkhtml.so.4
#30 0xb7d63f8f in QPtrDict<QWidget>::deleteItem () from /usr/lib/libkhtml.so.4
#31 0xb7d63d12 in QPtrDict<QWidget>::deleteItem () from /usr/lib/libkhtml.so.4
#32 0xb7d03103 in KHTMLView::dispatchMouseEvent () from /usr/lib/libkhtml.so.4
#33 0xb7cfd07e in KHTMLView::viewportMouseReleaseEvent ()
   from /usr/lib/libkhtml.so.4
#34 0xb6da0a10 in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#35 0xb7cfeca2 in KHTMLView::eventFilter () from /usr/lib/libkhtml.so.4
#36 0xb6c94b01 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#37 0xb6c94a5d in QObject::event () from /usr/lib/libqt-mt.so.3
#38 0xb6cca76f in QWidget::event () from /usr/lib/libqt-mt.so.3
#39 0xb6c3f370 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#40 0xb6c3eac7 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#41 0xb724a8a5 in KApplication::notify () from /usr/lib/libkdecore.so.4
#42 0xb6bd812f in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#43 0xb6bd5e1c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#44 0xb6bebec2 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#45 0xb6c5074c in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#46 0xb6c5060e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#47 0xb6c3f57b in QApplication::exec () from /usr/lib/libqt-mt.so.3
#48 0xb7fb42d9 in kdemain () from /usr/lib/libkdeinit_kcontrol.so
#49 0x080486fb in ?? ()
#50 0x00000007 in ?? ()
#51 0xbffffaa4 in ?? ()
#52 0xbffffa78 in ?? ()
#53 0xb65cc8c8 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#54 0xb65cc8c8 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#55 0x08048631 in ?? ()

---

