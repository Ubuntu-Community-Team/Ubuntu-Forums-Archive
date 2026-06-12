---
title: "Konqueror krashing"
date: 2005-11-11
forum: General Help
---

### Post by Jeff Eklund on 2005-11-11
Yepp, When I try to use it for filebrowsing, such as navigating through my ~ directory, it chrashes whenever I move my mouse-pointer over an icon or a directory. It works fine in web-browsing mode. Never happened before, started happening today.
I am using Breezy with KDE 3.5b2.
Konqueror crashes with 11 - SIGSEGV as the error flag. This is the backtrace log:
```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1208592160 (LWP 11496)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#4  0x4d91f95e in __gnu_cxx::__pool<true>::_M_reclaim_block ()
   from /usr/lib/libstdc++.so.6
#5  0xb784d92f in __gnu_cxx::__mt_alloc<std::string, __gnu_cxx::__common_pool_policy<__gnu_cxx::__pool, true> >::deallocate ()
   from /usr/lib/kde3/konq_sound.so
#6  0xb784cdee in KonqSoundPlayerImpl::mimeTypes ()
   from /usr/lib/kde3/konq_sound.so
#7  0x4b5fe92d in KonqIconViewWidget::slotOnItem () from /usr/lib/libkonq.so.4
#8  0x4b61dbba in KonqIconViewWidget::qt_invoke () from /usr/lib/libkonq.so.4
#9  0x4de64196 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0x4e1f87db in QIconView::onItem () from /usr/lib/libqt-mt.so.3
#11 0x4e0572f9 in QIconView::contentsMouseMoveEvent ()
   from /usr/lib/libqt-mt.so.3
#12 0x4b5f05a8 in KonqIconViewWidget::contentsMouseMoveEvent ()
   from /usr/lib/libkonq.so.4
#13 0x4df96507 in QScrollView::viewportMouseMoveEvent ()
   from /usr/lib/libqt-mt.so.3
#14 0x4df98f6c in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#15 0x4e04c7da in QIconView::eventFilter () from /usr/lib/libqt-mt.so.3
#16 0x4de611b2 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#17 0x4de61230 in QObject::event () from /usr/lib/libqt-mt.so.3
#18 0x4de9e9a8 in QWidget::event () from /usr/lib/libqt-mt.so.3
#19 0x4ddfb6c0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#20 0x4ddfbc40 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#21 0x4b84feec in KApplication::notify () from /usr/lib/libkdecore.so.4
#22 0x4dd8c565 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#23 0x4dd87a65 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#24 0x4dd85daf in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#25 0x4dd9f73f in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0x4de1343b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0x4de1335e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0x4ddfa353 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x4c0915ac in kdemain () from /usr/lib/libkdeinit_konqueror.so
#30 0xb7f86730 in kdeinitmain () from /usr/lib/kde3/konqueror.so
#31 0x0804e128 in ?? ()
#32 0x00000002 in ?? ()
#33 0x0812e4f0 in ?? ()
#34 0xbfe88158 in ?? ()
#35 0x0804e16c in ?? ()
#36 0x00000000 in ?? ()
#37 0x00000000 in ?? ()
#38 0x00000000 in ?? ()
#39 0x4d65e334 in free () from /lib/tls/i686/cmov/libc.so.6
#40 0x0804e70a in ?? ()
#41 0x00000000 in ?? ()
#42 0x00000001 in ?? ()
#43 0x0812def0 in ?? ()
#44 0x00000000 in ?? ()
#45 0x00000000 in ?? ()
#46 0x00000000 in ?? ()
#47 0x0812def4 in ?? ()
#48 0x00000000 in ?? ()
#49 0x00000000 in ?? ()
#50 0x00000000 in ?? ()
#51 0x00000001 in ?? ()
#52 0x00000002 in ?? ()
#53 0x00000008 in ?? ()
#54 0x0812dec8 in ?? ()
#55 0x0812decc in ?? ()
#56 0x0812ded6 in ?? ()
#57 0x00000000 in ?? ()
#58 0x00000001 in ?? ()
#59 0x0812dee3 in ?? ()
#60 0x00000000 in ?? ()
#61 0x00000000 in ?? ()
#62 0x0812def4 in ?? ()
#63 0x0812dee3 in ?? ()
#64 0x4d8117d0 in ?? () from /usr/lib/libX11.so.6
#65 0xbfe88418 in ?? ()
#66 0x08052500 in vtable for QCString ()
#67 0x0805b550 in ?? ()
#68 0x08052500 in vtable for QCString ()
#69 0x0805b540 in ?? ()
#70 0xbfe8820c in ?? ()
#71 0xbfe8828c in ?? ()
#72 0x0000000a in ?? ()
#73 0x00000055 in ?? ()
#74 0x00000000 in ?? ()
#75 0xbfe8828c in ?? ()
#76 0x00000000 in ?? ()
#77 0xbfe8820c in ?? ()
#78 0xbfe8828c in ?? ()
#79 0xbfe88418 in ?? ()
#80 0x0804ecfc in ?? ()
#81 0xffffffff in ?? ()
#82 0x00000000 in ?? ()
#83 0x0000000a in ?? ()
#84 0x00000000 in ?? ()
#85 0x00000000 in ?? ()
#86 0x00000000 in ?? ()
#87 0x00000000 in ?? ()
#88 0x00000000 in ?? ()
#89 0x00000000 in ?? ()
#90 0x00000000 in ?? ()
#91 0x00000000 in ?? ()
#92 0x00000000 in ?? ()
#93 0x00000000 in ?? ()
#94 0x00000000 in ?? ()
#95 0x00000000 in ?? ()
#96 0x00000000 in ?? ()
#97 0x00000000 in ?? ()
#98 0x00000000 in ?? ()
#99 0x00000000 in ?? ()
#100 0x00000000 in ?? ()
#101 0x00000000 in ?? ()
#102 0x00000000 in ?? ()
#103 0x00000000 in ?? ()
#104 0x00000000 in ?? ()
#105 0x00000000 in ?? ()
#106 0x00000000 in ?? ()
#107 0x00000000 in ?? ()
#108 0x00000000 in ?? ()
#109 0x00000000 in ?? ()
#110 0x00000000 in ?? ()
#111 0x00000000 in ?? ()
#112 0x00000000 in ?? ()
#113 0x00000000 in ?? ()
#114 0x00000000 in ?? ()
#115 0x00000000 in ?? ()
#116 0x00000000 in ?? ()
#117 0x00000000 in ?? ()
#118 0x00000000 in ?? ()
#119 0x00000000 in ?? ()
#120 0x00000000 in ?? ()
#121 0x00000000 in ?? ()
#122 0x00000000 in ?? ()
#123 0x00000000 in ?? ()
#124 0x00000000 in ?? ()
#125 0x00000000 in ?? ()
#126 0x00000000 in ?? ()
#127 0x00000000 in ?? ()
#128 0x00000000 in ?? ()
#129 0x00000000 in ?? ()
#130 0x00000000 in ?? ()
#131 0x00000000 in ?? ()
#132 0x00000000 in ?? ()
#133 0x00000000 in ?? ()
#134 0x00000000 in ?? ()
#135 0x00000000 in ?? ()
#136 0x00000000 in ?? ()
#137 0x00000000 in ?? ()
#138 0x00000000 in ?? ()
#139 0x00000000 in ?? ()
#140 0x00000000 in ?? ()
#141 0x00000000 in ?? ()
#142 0x00000000 in ?? ()
#143 0x00000000 in ?? ()
#144 0x00000000 in ?? ()
#145 0x00000000 in ?? ()
#146 0x00000000 in ?? ()
#147 0x00000000 in ?? ()
#148 0x00000100 in ?? ()
#149 0x00000000 in ?? ()
#150 0x00000000 in ?? ()
#151 0x00000000 in ?? ()
#152 0x00000000 in ?? ()
#153 0x00000000 in ?? ()
#154 0x00000000 in ?? ()
#155 0x00000000 in ?? ()
#156 0x00000000 in ?? ()
#157 0x00000000 in ?? ()
#158 0x00000000 in ?? ()
#159 0x00000000 in ?? ()
#160 0x00000000 in ?? ()
#161 0x00000000 in ?? ()
#162 0x00000000 in ?? ()
#163 0x00000000 in ?? ()
#164 0x00000000 in ?? ()
#165 0x00000000 in ?? ()
#166 0x00000000 in ?? ()
#167 0x00000000 in ?? ()
#168 0x00000000 in ?? ()
#169 0x00000000 in ?? ()
#170 0x00000000 in ?? ()
#171 0x00000000 in ?? ()
#172 0x00000000 in ?? ()
#173 0x00000000 in ?? ()
#174 0x00000000 in ?? ()
#175 0x00000000 in ?? ()
#176 0x00000000 in ?? ()
#177 0x00000000 in ?? ()
#178 0x00000000 in ?? ()
#179 0x00000000 in ?? ()
#180 0x00002c86 in ?? ()
#181 0x00000000 in ?? ()
#182 0x00000001 in ?? ()
#183 0x0805e410 in ?? ()
#184 0x00600001 in ?? ()
#185 0x000001f6 in ?? ()
#186 0x00000020 in ?? ()
#187 0x00000000 in ?? ()
#188 0x00000000 in ?? ()
#189 0x00000000 in ?? ()
#190 0x00000000 in ?? ()
#191 0x00000000 in ?? ()
#192 0x00000000 in ?? ()
#193 0x00000000 in ?? ()
#194 0x00000000 in ?? ()
#195 0x00000000 in ?? ()
#196 0x00000000 in ?? ()
#197 0x00000000 in ?? ()
#198 0x00000000 in ?? ()
#199 0x00000000 in ?? ()
#200 0x00000000 in ?? ()
#201 0x00000000 in ?? ()
#202 0x00000000 in ?? ()
#203 0x00000000 in ?? ()
#204 0x00000000 in ?? ()
#205 0x4d7250dc in ?? () from /lib/tls/i686/cmov/libc.so.6
#206 0x4d726900 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#207 0x0805b540 in ?? ()
#208 0x00000003 in ?? ()
#209 0x00000008 in ?? ()
#210 0x00000002 in ?? ()
#211 0x00e885b8 in ?? ()
#212 0x00000002 in ?? ()
#213 0x0805b560 in ?? ()
#214 0x0805e410 in ?? ()
#215 0xbfe885b8 in ?? ()
#216 0x0804fbf1 in ?? ()
#217 0x00000004 in ?? ()
#218 0xbfe885ab in ?? ()
#219 0x00000001 in ?? ()
#220 0xbfe89fea in ?? ()
#221 0x4d660391 in malloc () from /lib/tls/i686/cmov/libc.so.6

``` Any ideas anyone?
Thnaks!

---

### Post by Basu on 2005-11-11
Konqueror crashes regularly on 3.4 too. I think that you might be consider a separate file browser.

---

### Post by asimon on 2005-11-11
```

#4  0x4d91f95e in __gnu_cxx::__pool<true>::_M_reclaim_block ()
   from /usr/lib/libstdc++.so.6
#5  0xb784d92f in __gnu_cxx::__mt_alloc<std::string, __gnu_cxx::__common_pool_policy<__gnu_cxx::__pool, true> >::deallocate ()
   from /usr/lib/kde3/konq_sound.so

```
From these two lines it looks like somehow the system sounds (konq_sound.so) is involved in the crash, i.e. arts. Then it would be a [known problem for the KDE 3.5 beta](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems). At least line #4 is identically to the known arts crash (I think others have the desktop crashing if they hover the mouse cursor above a desktop icon). If you don't want to wait until the next beta update you could try downgrade arts and look if the crash still happens. The wiki page has some instructions how to downgrade arts, there must also be some threads about this topic burried here somewhere.

---

### Post by Jeff Eklund on 2005-11-11
I did have the arts problem before too, but I donwgraded arts and everything except knotify is working. Knotify dosent give me any error messages, dosen't crash or anything, it just dosen't sound.
Mt arts version is 1.4.91-0ubuntu1, and the strange thing is that I fixed the arts problem last week, at the same time as I upgraded my KDE version to 3.5b2 and konqueror's been working like a charm up until now. And I haven't changed anything!
This really bugs me...

---

### Post by DoeRayMe on 2005-11-11
If the bugs are *bugging* you, maybe the beta, is'nt right for you

Just my opinion

btw im on Beta 2, my Konqueror only crashes when i try to preview something

hope that helps

---

### Post by Jeff Eklund on 2005-11-11
No, the bugs dosen't bug me. As I said, konqueror worked perfectly yeasterday. Filepreviews and everything. What bugs me is that it started crashing now, even though I haven't altered the system in any way.

---

### Post by DoeRayMe on 2005-11-11
No updates? anyone else been on the computer, Try turning off the System Sounds and see if it still happens

---

### Post by asimon on 2005-11-11
[QUOTE=Jeff Eklund]What bugs me is that it started crashing now, even though I haven't altered the system in any way.[/QUOTE]
Maybe you have changed some preferences or settings? After all there must be a reason why it crashes today but didn't yesterday. It could be something which is triggered only with certain settings.

---

### Post by Jeff Eklund on 2005-11-11
No updates. I updated FreeCiv, but I doubt that had anything to do with it?
Turning off the system sounds, sounds like a good idea. How would i go about doing that? I can't seem to find any entry for shutting down the soundserver in my controlpanel?

---

### Post by DoeRayMe on 2005-11-11
right if you havent got an entery for the Control Panel, press Run Command and type "kcontrol" without the quotes though, then go to "Sound & Multimedia"  and choose "Sound System" and then uncheck "Enable the sound system"

---

### Post by Jeff Eklund on 2005-11-11
I do have an entry for my Kcontrol, I just didn't find the "Enable soundsystem" option when browsing the controls. It was too big and obvious.
I tried it and it worked. Konqueror stopped crashing. Thanks! 
But explain this to me: I thought that when I switched the soundserver off, I wouldn't be able to hear any sounds, right? I still do. I haven't rebooted my computer, but I've tried restarting for example amaroK and it still plays music without any troubles. Is this beacuse I haven't rebooted and the system hasn't reloaded the drivers or something like that, or what does the "Enable soundsystem"-option actually switch?

---

### Post by DoeRayMe on 2005-11-11
I thought the same, but the option only enables/disables the system sounds, like shutting down sound and other program sounds, but music players still work through alsa or esd or w/e

---

### Post by Jeff Eklund on 2005-11-11
Okey, that's good to know. Thanks alot for all your help! :-)

---

### Post by jesse on 2005-11-11
I'm also using kde 3.5b2 with Kubuntu. 

I have disabled the kde sound system, too, because I find that when it's enabled there are a lot of crashes and also when it's enabled whenever I try to use any application with sound I get an error message saying something like "sound system busy, another program [i.e. the kde soundsystem!] may be using it."

Although I have the kde sound system disabled, I still have my system sounds working because I use mplayer for them. It works great. 

To use mplayer as the engine for the system sounds (start up jingle, etc) just go to "sound and multimedia" in the control center and go the submenu "system sounds." Then click on "player settings," choose use external player and type "mplayer" in the box to make it the player. As long as mplayer is installed it can play the system sounds just as easily as the kde sound system but unlike the kde system mplayer won't block other programs from using sound as frequently. 

You never see any gui pop up and so you never know it's mplayer playing the system sounds. I wish they would make mplayer the default system sound engine for kde.

---

### Post by asimon on 2005-11-12
[QUOTE=Jeff Eklund]But explain this to me: I thought that when I switched the soundserver off, I wouldn't be able to hear any sounds, right? I still do. I haven't rebooted my computer, but I've tried restarting for example amaroK and it still plays music without any troubles[/QUOTE]
It's because amaroK doesn't use this soundserver. It's mostly used for playing system sounds, like sounds you can have for various window manager actions (you know, annoying sounds when a window opens or closes, etc.), or for notification sounds of some apps (like kopete). AmaroK doesn't use this, it uses gstreamer, xine, or whatever you configured it to use. Maybe amarok doesn't work when you configured it to use arts, which is the sound server for the KDE system sounds (but it could also be that in this case amaroK starts arts by itself, I haven't tried it).

So if you have the "soundserver" off, you probably won't get any system sounds but apps like amarok will still have sound. To still have system sounds, even when not using arts, see the posting from Jesse. BTW, this horrible sound server arts will go away for KDE 4. Better times are coming ...

---

### Post by Jeff Eklund on 2005-11-12
> **jesse]To use mplayer as the engine for the system sounds (start up jingle, etc) just go to &quot said:**
> Great tip! Thanks alot!
[quote=asimon]It's because amaroK doesn't use this soundserver. It uses gstreamer, xine, or whatever you configured it to use.I figured it might be something like that, but then someone told me that the arts-server was the main-server through which all other, &quot;smaller&quot;, soundservers where handled, so that ie the gstreamer-server (which I'm using in amaroK) was started and handled through the arts-server (May sound crazy to you, but I'm no expert in how KDE is built and configured)[quote=asimon]BTW, this horrible sound server arts will go away for KDE 4. Better times are coming ...[/quote]Yes, I've heard people talking about KDE4 not using arts. What server will it use?

Thanks again for all of your help!

---

