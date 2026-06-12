---
title: "Akregator crashes when i try to run it"
date: 2008-09-09
forum: General Help
---

### Post by Bandit09 on 2008-09-09
Hello everyone, When I try to run Akregator it crashes immediately with a signal 11. Here is the backtrace:

> (no debugging symbols found)
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
[Thread debugging using libthread_db enabled]
[New Thread 0xb5dfd6c0 (LWP 29838)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb5ebd9bc in memcpy () from /lib/tls/i686/cmov/libc.so.6
#7  0xb585971b in c4_Column::FetchBytes ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#8  0xb5862868 in c4_FormatB::GetOne ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#9  0xb58628b0 in c4_FormatS::Get ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#10 0xb58656b5 in c4_Handler::GetBytes ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#11 0xb5873a77 in c4_Sequence::Get ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#12 0xb5870c78 in c4_View::GetItem ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#13 0xb5869e75 in c4_HashViewer::GetItem ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#14 0xb5859da9 in c4_CustomSeq::DoGet ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#15 0xb585aa77 in c4_CustomHandler::Get ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#16 0xb58656b5 in c4_Handler::GetBytes ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#17 0xb5873a77 in c4_Sequence::Get ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#18 0xb5874a85 in c4_StringRef::operator char const* ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#19 0xb5851c93 in Akregator::Backend::FeedStorageMK4Impl::articles ()
   from /usr/lib/kde3/libakregator_mk4storage_plugin.so
#20 0xb7f00917 in Akregator::Feed::loadArticles ()
   from /usr/lib/libakregatorprivate.so
#21 0xb7f0181b in Akregator::Feed::fromOPML ()
   from /usr/lib/libakregatorprivate.so
#22 0xb7f0bec5 in Akregator::FeedList::parseChildNodes ()
   from /usr/lib/libakregatorprivate.so
#23 0xb7f0bfcc in Akregator::FeedList::parseChildNodes ()
   from /usr/lib/libakregatorprivate.so
#24 0xb7f0c48e in Akregator::FeedList::readFromXML ()
   from /usr/lib/libakregatorprivate.so
#25 0xb5aa3229 in Akregator::View::loadFeeds ()
   from /usr/lib/kde3/libakregatorpart.so
#26 0xb5a9e838 in Akregator::Part::openFile ()
   from /usr/lib/kde3/libakregatorpart.so
#27 0xb5a9c60c in Akregator::Part::openURL ()
   from /usr/lib/kde3/libakregatorpart.so
#28 0xb5a98874 in Akregator::Part::openStandardFeedList ()
   from /usr/lib/kde3/libakregatorpart.so
#29 0xb5aae80e in Akregator::AkregatorPartIface::process ()
   from /usr/lib/kde3/libakregatorpart.so
#30 0xb6c3d310 in DCOPClient::receive () from /usr/lib/libDCOP.so.4
#31 0xb6c403b2 in DCOPClient::send () from /usr/lib/libDCOP.so.4
#32 0xb6c409df in DCOPRef::sendInternal () from /usr/lib/libDCOP.so.4
#33 0x080513aa in ?? ()
#34 0xb6dd3516 in KUniqueApplication::processDelayed ()
   from /usr/lib/libkdecore.so.4
#35 0xb6dee243 in KUniqueApplication::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#36 0xb66b8704 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#37 0xb6a47aba in QSignal::signal () from /usr/lib/libqt-mt.so.3
#38 0xb66d77b2 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#39 0xb66df936 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#40 0xb664cc36 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb664ea5f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb6e0d9b2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb65dd28d in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#44 0xb663fb19 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#45 0xb65f264b in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#46 0xb6667f90 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#47 0xb6667c8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#48 0xb664e7df in QApplication::exec () from /usr/lib/libqt-mt.so.3
#49 0x08050e53 in ?? ()
#50 0xb5e60450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#51 0x08050d01 in ?? ()



I have no idea with this means, if anyone could help me get akregator working again I'd greatly appreciate it.

Thank you!

---

### Post by Neo_The_User on 2008-09-09
Where could I download a deb for Akregator so I can help you? And which version of Akregator and kde are you using?

---

### Post by Bandit09 on 2008-09-09
I am using the newest version of KDE in the 3.x series, as well as the newest akregator version. you can install it just by doing apt-get akregator, i believe it's in the default repositories. I appreciate your help :-)

---

