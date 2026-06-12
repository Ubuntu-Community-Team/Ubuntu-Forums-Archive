---
title: "Tried updating KDE4 4.0.3 to 4.1.2...BIG PROBLEM!"
date: 2008-10-21
forum: General Help
---

### Post by Moonfrost on 2008-10-21
What the title says. It updated everything without problems so I went and restarted the computer and then the new login screen appeared, I logged in and it said "KDE 4.1" instead of "4.0" which means it updated successfully of course, but when it was trying to login it says that there's a fatal error and that plasma won't load, also the startup sound starts but it cuts off and shows me a message on the top right corner of the screen that the HNVIDIA (or something like that) the sound output device is not working and then says that it's switching to another one (long name also involving nvidia and lots of numbers) that between parenthesis it says (Analog). 

Here's the error message, I'm typing this from Firefox which I launched using Alt+F2 because I'm not dual-booting right now.

```
The application Plasma Workspace (plasma) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at http://bugs.kde.org. Useful details include how to reproduce the error, documents that were loaded, etc.
```

EDIT: This is what appears when I just type "plasma" on konsole, quite a lot of errors/problems which I have no idea about...specially considering I'm not familiar with plasma since it's new in KDE4 and I haven't used KDE4 that many times:

```
moonfrost@moonfrost-desktop:~$ plasma
<unknown program name>(7070)/ checkComposite: Plasma has an argb visual 0x624f00 52428801
<unknown program name>(7070)/ checkComposite: Plasma is COMPOSITE-less on 0x61c0f0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x320000a
Plasma crashed, attempting to automatically recover
<unknown program name>(7074)/ checkComposite: Plasma has an argb visual 0x624f00 56623105
<unknown program name>(7074)/ checkComposite: Plasma is COMPOSITE-less on 0x61c0f0
plasma(7070): Communication problem with  "plasma" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

moonfrost@moonfrost-desktop:~$ KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = plasma path = <unknown> pid = 7071
sock_file=/home/moonfrost/.kde4/socket-moonfrost-desktop/kdeinit4__0
plasma(7074): KUniqueApplication: Registering failed!

plasma(7074): Communication problem with  "plasma" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.plasmawas not provided by any .service files" "
```

EDIT #2: I also opened adept using the same Alt+F2 method to open it, I typed plasma and then chose to reinstall...I did a restart and the same thing happens...

EDIT#3: On the error message this time I clicked details and then copied the whole text (the message prompt gives an option to do it without me having to scroll the whole thing to select it) and this is what it shows:

```
Application: Plasma Workspace (plasma), signal SIGSEGV
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread 0x7f315b4987e0 (LWP 5909)]
[New Thread 0x4196c950 (LWP 5910)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#5  0x00007f315910bc9f in QGraphicsLinearLayout::insertItem ()
   from /usr/lib/libQtGui.so.4
#6  0x00007f3149c73815 in ?? ()
   from /usr/lib/kde4/lib/kde4/plasma_applet_devicenotifier.so
#7  0x00007f3149c73a1c in ?? ()
   from /usr/lib/kde4/lib/kde4/plasma_applet_devicenotifier.so
#8  0x00007f315abb59f0 in Plasma::Applet::flushPendingConstraintsEvents ()
   from /usr/lib/kde4/lib/libplasma.so.2
#9  0x00007f3159e321d5 in QObject::event () from /usr/lib/libQtCore.so.4
#10 0x00007f315910df2b in QGraphicsWidget::event ()
   from /usr/lib/libQtGui.so.4
#11 0x00007f3158bbdacf in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#12 0x00007f3158bbfc85 in QApplication::notify () from /usr/lib/libQtGui.so.4
#13 0x00007f315a73a1f1 in KApplication::notify ()
   from /usr/lib/kde4/lib/libkdeui.so.5
#14 0x00007f3159e236b9 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#15 0x00007f3159e4ea0c in ?? () from /usr/lib/libQtCore.so.4
#16 0x00007f3159e4c57d in ?? () from /usr/lib/libQtCore.so.4
#17 0x00007f31548b43d4 in g_main_context_dispatch ()
   from /usr/lib/libglib-2.0.so.0
#18 0x00007f31548b76e5 in ?? () from /usr/lib/libglib-2.0.so.0
#19 0x00007f31548b7bcb in g_main_context_iteration ()
   from /usr/lib/libglib-2.0.so.0
#20 0x00007f3159e4c9df in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#21 0x00007f3158c4720f in ?? () from /usr/lib/libQtGui.so.4
#22 0x00007f3159e22b35 in QEventLoop::processEvents ()
   from /usr/lib/libQtCore.so.4
#23 0x00007f3159e22c8b in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#24 0x00007f31583ae684 in KIO::NetAccess::enter_loop ()
   from /usr/lib/kde4/lib/libkio.so.5
#25 0x00007f31583aeb55 in KIO::NetAccess::statInternal ()
   from /usr/lib/kde4/lib/libkio.so.5
#26 0x00007f31583af10e in KIO::NetAccess::stat ()
   from /usr/lib/kde4/lib/libkio.so.5
#27 0x00007f31583af1bf in KIO::NetAccess::mostLocalUrl ()
   from /usr/lib/kde4/lib/libkio.so.5
#28 0x00007f314af7608e in ?? ()
   from /usr/lib/kde4/lib/kde4/plasma_applet_icon.so
#29 0x00007f314af76e50 in ?? ()
   from /usr/lib/kde4/lib/kde4/plasma_applet_icon.so
#30 0x00007f315abe01d7 in Plasma::Corona::loadLayout ()
   from /usr/lib/kde4/lib/libplasma.so.2
#31 0x00007f315abe030e in Plasma::Corona::initializeLayout ()
   from /usr/lib/kde4/lib/libplasma.so.2
#32 0x00007f315b2641e2 in ?? () from /usr/lib/kde4/lib/libkdeinit4_plasma.so
#33 0x00007f315b2654c3 in ?? () from /usr/lib/kde4/lib/libkdeinit4_plasma.so
#34 0x00007f315b265c52 in ?? () from /usr/lib/kde4/lib/libkdeinit4_plasma.so
#35 0x00007f315b25ae59 in kdemain ()
   from /usr/lib/kde4/lib/libkdeinit4_plasma.so
#36 0x00007f315aefb1c4 in __libc_start_main () from /lib/libc.so.6
#37 0x0000000000400649 in _start ()
#0  0x00007f315af7ab81 in nanosleep () from /lib/libc.so.6
```

Hope all this info helps.

---

### Post by Moonfrost on 2008-10-21
Uh...anyone?

EDIT: Fixed it by deleting the plasma config file at /home/username/.kde4/share/config/plasma-appletssrc, I saw that solution on some post on the KDE bug site and everything is working fine now, but my sound it's still not working and I have no idea if it's related to the other problem at all...if it's not then there's some OTHER problem which would mean this latest KDE release is less stable than 4.0.3 which I had before (was stable as a rock).

EDIT#2: Sound works, I just didn't know that they had removed the nice minimize/maximize and desktop switching sounds.

---

