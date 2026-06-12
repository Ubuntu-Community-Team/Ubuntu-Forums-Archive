---
title: "Plasma segfaults and no network after upgrade to KDE 4.3.1"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by WindPower on 2009-09-02
Using Kubuntu 9.04 Jaunty 64-bit, I just upgraded from KDE 4.2 to KDE 4.3.1 using the kubuntu-backports PPA on launchpad. After restarting, I can get to the login manager fine, but instead of my desktop showing up, plasma segfaults.
```
Application: Plasma Workspace (plasma), signal: Segmentation fault
[KCrash Handler]
#5  0x00007fce04552f60 in ?? () from /usr/lib/libsolidcontrol.so.4
#6  0x00007fce0455b66d in ?? () from /usr/lib/libsolidcontrol.so.4
#7  0x00007fce04555826 in ?? () from /usr/lib/libsolidcontrol.so.4
#8  0x00007fce04555dc4 in ?? () from /usr/lib/libsolidcontrol.so.4
#9  0x00007fce04555f4c in ?? () from /usr/lib/libsolidcontrol.so.4
#10 0x00007fce04555fdc in Solid::Control::NetworkManager::networkInterfaces () from /usr/lib/libsolidcontrol.so.4
#11 0x00007fce0253bcc9 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#12 0x00007fce0253db04 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#13 0x00007fce02541967 in KPluginFactory::createInstance<NetworkManagerApplet, QObject> () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#14 0x00007fce1ed965ad in KPluginFactory::create () from /usr/lib/libkdecore.so.5
#15 0x00007fce20815f06 in Plasma::Applet::load () from /usr/lib/libplasma.so.3
#16 0x00007fce208249e0 in ?? () from /usr/lib/libplasma.so.3
#17 0x00007fce20827919 in Plasma::Containment::restoreContents () from /usr/lib/libplasma.so.3
#18 0x00007fce20829e63 in Plasma::Containment::restore () from /usr/lib/libplasma.so.3
#19 0x00007fce2082d089 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.3
#20 0x00007fce2082eb92 in Plasma::Corona::initializeLayout () from /usr/lib/libplasma.so.3
#21 0x00007fce20bd3a17 in ?? () from /usr/lib/libkdeinit4_plasma.so
#22 0x00007fce20bd4025 in ?? () from /usr/lib/libkdeinit4_plasma.so
#23 0x00007fce20bd7088 in ?? () from /usr/lib/libkdeinit4_plasma.so
#24 0x00007fce1c492ea2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#25 0x00007fce1c49814f in ?? () from /usr/lib/libQtCore.so.4
#26 0x00007fce1c48d263 in QObject::event () from /usr/lib/libQtCore.so.4
#27 0x00007fce1cb86f4d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#28 0x00007fce1cb8f18a in QApplication::notify () from /usr/lib/libQtGui.so.4
#29 0x00007fce1f22cdeb in KApplication::notify () from /usr/lib/libkdeui.so.5
#30 0x00007fce1c47d6ac in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#31 0x00007fce1c4aa516 in ?? () from /usr/lib/libQtCore.so.4
#32 0x00007fce1c4a6b2d in ?? () from /usr/lib/libQtCore.so.4
#33 0x00007fce16ef820a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#34 0x00007fce16efb8e0 in ?? () from /usr/lib/libglib-2.0.so.0
#35 0x00007fce16efba7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#36 0x00007fce1c4a6a8f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#37 0x00007fce1cc1fbdf in ?? () from /usr/lib/libQtGui.so.4
#38 0x00007fce1c47bf42 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#39 0x00007fce1c47c314 in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#40 0x00007fce1c47e5e4 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#41 0x00007fce20bc19bb in kdemain () from /usr/lib/libkdeinit4_plasma.so
#42 0x00007fce1b8375a6 in __libc_start_main () from /lib/libc.so.6
#43 0x00000000004007c9 in _start ()
```
If I launch it from a terminal, I get this:
```
$ plasma
<unknown program name>(2015)/ checkComposite: Plasma has an argb visual 0x6ea430 16777217
<unknown program name>(2015)/ checkComposite: Plasma can use COMPOSITE for effects on 0x6deec0
could not access kephald, falling back to QDesktopWidget
adding an output 0 with geom:  QRect(0,0 1366x768)
Object::connect: No such signal NMWiredNetworkInterface::connectionStateChanged(int,int,int)
Object::connect: No such signal NMWirelessNetworkInterface::connectionStateChanged(int,int,int)
<unknown program name>(2088)/ checkComposite: Plasma has an argb visual 0x75e430 31457281
<unknown program name>(2088)/ checkComposite: Plasma can use COMPOSITE for effects on 0x752ec0
KCrash: Application 'plasma' crashing...
sock_file=/home/(username)/.kde/socket-(computer name)/kdeinit4__0
```

So now I've got a completely black desktop, but it is still functional: I can launch stuff from the command line or launch Firefox with hotkeys I've set up in Compiz (which still works as well, only with black desktops).

Along with the plasma crash, I seem to have lost any possible way to connect to the Internet. My ethernet connection never worked (and [my thread about it](http://ubuntuforums.org/showthread.php?t=1207928) didn't get any reply), but the wireless used to work... but not anymore now. Note that it broke right after I upgraded to KDE 4.3.1 (before rebooting), and I assumed a reboot would fix it, but apparently it didn't, so now I'm kind of stuck with no desktop and no network. :( How can I get it to work? If it involves downgrading back to KDE 4.2, that's fine, but I have no network so I'm kind of stuck here.

---

### Post by pablored on 2009-09-03
I have the same plasma 4.3.1 issue on a fresh install (64 bit).

Plasma was held back in the apt upgrade, among other things, maybe something is up with all the 64bit packages.

Someone else with the same issue:

[http://ubuntuforums.org/showthread.php?t=1256180&highlight=plasma](http://ubuntuforums.org/showthread.php?t=1256180&highlight=plasma)

---

### Post by Ubuntiac on 2009-09-03
Sometimes when I've had issues with packages being held back, I've found that the following has helped:
```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install kubuntu-desktop
```

The last part just makes sure that all the KDE dependencies are installed. Sometimes a dist-upgrade seems to end up removing some needed dependencies (usually kdeworkspace-bin).

---

### Post by pablored on 2009-09-03
```
sudo apt-get update && sudo apt-get dist-upgrade &**&** sudo apt-get install kubuntu-desktop
```

Works.. with the extra ampersand.  Cheers.

I am not currently using wireless, so I had no network issues getting the upgrades.

---

### Post by Ubuntiac on 2009-09-03
Glad it worked for you! The first time I had this took me hours to find a solution. I've added the extra ampersand for futre people reading this. Thanks for pointing that out!

---

### Post by WindPower on 2009-09-03
Well, seems like the package installation didn't go all the way through, and a dpkg reconfigure seems to have fixed most things up, despite producing many warnings about broken packages and missing dependencies...
At least I got my desktop back, from the most part. But it has lots of new glitches now :(
For one, my background won't show up right when the desktop is loaded; I have to go to the Desktop settings and click "OK" so that it forces the desktop background to refresh itself.
Second, I have lost my transparent panel. Now it's back to the Blueish opaque gradient, even though the settings say Compositing is active.
Third, I have lost all window borders and titlebars. Switching the window borders to anything else than Oxygen brings them back, but they look ugly :(
Fourth, the pager stopped working. It used to have 4 buttons, one for each side of the cube, now it's only got one. I can still swich from a cube face to another with the Compiz hotkeys though.
Fifth, the login screen looks terrible. I do see the nice blueish background and the light login box and all, but on the side of the screen, I see gibberish spots of green and red dots, all mixed up, as if the login background had not been designed for my resolution (1366x768 px) or aspect ratio: it's like a letterbox, but with random colors instead of black. :o

---

### Post by Ubuntiac on 2009-09-03
Hmmm... this is getting beyond my meagre skills. In your shoes I'd usually just *repeatedly* do the following until I didn't get any more errors in the console:

> sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo dpkg --configure -a && sudo apt-get -f install && sudo apt-get install kubuntu-desktop


I call this my "universal fix it or destroy it forver" code.
Beyond this, I'd be posting here and searching Google.

May the Force be with You.

---

