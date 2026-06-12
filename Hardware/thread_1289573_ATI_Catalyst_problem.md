---
title: "ATI Catalyst problem"
date: 2009-10-12
forum: Hardware
---

### Post by wekya on 2009-10-12
Help!! I don't want to have to go back to windoze!!

This is a fresh Linux Mint Gloria install (which is a Jaunty 9.04 clone) with all updates. The only other program I've added is VLC.

I have installed the Radeon latest (ATI Catalyst™ 9.8 Proprietary Linux x86 Display Driver v9.9), after I had used Envy to add and enable the ATI drivers. I did this via CLI and the 9.9 seemed to go well. Now catalyst appears in my program menu, but when I click on it to open it nothing happens. Envy shows I have the recommended version 8.600 0ubuntu2 running but when I close it after checking it says "The application envyNG crashed and caused the signal 11 (SIGSEGV). With this debug info:

[HTML]This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d596c0 (LWP 4080)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f2e430 in __kernel_vsyscall ()
[Current thread is 0 (process 4080)]
Thread 1 (Thread 0xb7d596c0 (LWP 4080)):
#0 0xb7f2e430 in __kernel_vsyscall ()
#1 0xb7f10013 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2 0xb4e1718f in ?? () from /usr/lib/libkdeui.so.5
#3 0xb4e180e3 in KCrash::defaultCrashHandler () from /usr/lib/libkdeui.so.5
#4 <signal handler called>
#5 0xb64e5b82 in ?? () from /usr/lib/libQtGui.so.4
#6 0xb64debb6 in ?? () from /usr/lib/libQtGui.so.4
#7 0xb6312066 in QWidgetPrivate::deleteExtra () from /usr/lib/libQtGui.so.4
#8 0xb6312845 in QWidgetPrivate::~QWidgetPrivate () from /usr/lib/libQtGui.so.4
#9 0xb67c7a79 in ?? () from /usr/lib/libQtGui.so.4
#10 0xb73332e1 in QObject::~QObject () from /usr/lib/libQtCore.so.4
#11 0xb631784f in QWidget::~QWidget () from /usr/lib/libQtGui.so.4
#12 0xb67df776 in QDialog::~QDialog () from /usr/lib/libQtGui.so.4
#13 0xb6fd9cb5 in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#14 0xb6f7df8c in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#15 0xb6f7dfce in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#16 0xb71c75a3 in ?? () from /usr/lib/python2.6/dist-packages/sip.so
#17 0x080a90d5 in ?? ()
#18 0x0808cb61 in ?? ()
#19 0x0808ee69 in PyDict_SetItem ()
#20 0x080909c1 in _PyModule_Clear ()
#21 0x080f17a2 in PyImport_Cleanup ()
#22 0x080fd90d in Py_Finalize ()
#23 0x0805c129 in Py_Main ()
#24 0x0805b972 in main ()
#0 0xb7f2e430 in __kernel_vsyscall ()[/HTML]



Hardware drivers shows the fglxr is enabled. When I "sudo gedit /etc/X11/xorg.conf " from the wiki here:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) ... tion_Guide

it looks OK with the driver being listed as "fglrx",...
but when I try aticonfig --initial -f I get the error message;

"Parse error on line 34 of section Module in file /etc/X11/xorg.conf
"Disable" is not a valid keyword in this section.

I don't know if that is because my card has D-sub, HDMI, and DVI outputs (with only the HDMI plugged in).

So then I try to "force the use of /etc/Xorg.conf file" (step 7 in the Jaunty install ATI wiki)....and it tells me:

Could not find configuration file
Please copy configuration file template to /etc/X11

but it still tells me it knows my card is there and has all the good stuff by saying;

[HTML]glrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3450
OpenGL version string: 2.1.8918[/HTML]


With all of this blah blah blah it is outputting beautifully....except....there is a 1 inch band of black all around the desktop (bad for image retention on the plasma!!), plus the whole computer seems to be working much slower with the new vid card. I hoped this new card would allow better playback of monster .mkv files. My older single core CPU needs help in this regard. Videos (the main thing I use this box for) stutter and play like poop now with this new card and fresh Gloria install. The old Nvidia 5200 (256RAM) worked much better under Gloria. I did use this box for the past couple of weeks with Win XP and the card was almost smoothly playing blueray .mkv rips so I know it's the devil's details here. I want to get catalyst to open so I can tweak the settings to eliminate the 1" border and see if it can allow OC (doubt it) like in the windoze version. I find it strange Catalyst is shown in the program menu, but just won't open. I can open the Gnome display window, but it lacks the granularity I know Catalyst will provide to let me adjust the overscan so I can have the complete screen filled.

I'm at a loss for what to do next. If you have ideas that'll help me please spoon feed me point by point. Assume I know nothing except how to turn it on. I even go to root to do all of the above CLI things because I'm afraid to sudo when in user mode. So how can I get catalyst to open? Does anyone else have this problem? Is there any command people know to FORCE catalyst to open?

---

### Post by markbuntu on 2009-10-13
I have never had any luck with envy myself. The catalyst control center will not open if the driver is misinstalled.

the aticonfig command needs to be run as root

sudo aticonfig --initial -f

This will make a new xorg.conf file.
reboot, do not forget to reboot.

If all else fails, use envy to remove the driver and, if you installed a driver using hardware manager, use the Synaptic package manager to remove anything with fglrx in it. Then download the latest driver from the ati site and run the installer

sudo sh ./ati-driver-installer----(fill in the rest yourself)

just let the automatic installer run and hit enter when it asks you what you want to do.

Then run

sudo aticonfig --initial -f

reboot. 
I have a HD3650 and a HD3450 and have not had any problems for quite a while. If you have a laptop you have a mobility HD3450 and that needs the latest Catalyst 9.9 driver

---

