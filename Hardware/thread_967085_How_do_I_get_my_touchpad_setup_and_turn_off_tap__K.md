---
title: "How do I get my touchpad setup and turn off tap  Kubuntu 8.10"
date: 2008-11-01
forum: Hardware
---

### Post by sspletttstoeszer on 2008-11-01
I'm new  to Linux! I just installed Kubuntu 8.10 and I got my wireless network working and I installed gsynaptics but I can't find it.
I don't know the terminal thing very well so I will need a step by step on what to do. I tried some think I found but this is what I got.

scott@scottspc:~$ sudo apt-get install gsynaptics
[sudo] password for scott:                       
Reading package lists... Done                   
Building dependency tree                         
Reading state information... Done               
gsynaptics is already the newest version.       
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@scottspc:~$ sudo kate /etc/xorg.conf
Error: "/var/tmp/kdecache-scott" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-scott" is owned by uid 1000 instead of uid 0.         
kate(6873): createDoc                                                 
kate(6873) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/home/scott/.kde/share/apps/kate/sessions"                                             
kate(6873) KateApp::initKate: Setting KATE_PID: ' 6873 '                       
kate(6873) KateViewDocumentProxyModel::updateBackgrounds: false                 
kate(6873) KateMainWindow::KateMainWindow: **************************************************************************** 0x2066ef0                               
kate(6873) KateViewDocumentProxyModel::updateBackgrounds: false                 
kate(6873) KateViewDocumentProxyModel::updateBackgrounds: false                 
kate(6873) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(6873) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "xorg.conf"
Error: "/tmp/ksocket-scott" is owned by uid 1000 instead of uid 0.
kate(6873) KToolInvocation::klauncher: klauncher not running... launching kdeinit
Error: "/tmp/kde-scott" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-scott" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
Error: "/tmp/ksocket-scott" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-scott" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kded4
Error: "/var/tmp/kdecache-scott" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-scott" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-scott" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch
kate(6873) KateViewDocumentProxyModel::updateBackgrounds: true
kdeinit4: preparing to launch /usr/bin/knotify4
Error: "/var/tmp/kdecache-scott" is owned by uid 1000 instead of uid 0.
kate(6873): Couldn't start knotify from knotify4.desktop:  "KDEInit could not launch '/usr/bin/knotify4'."

kate(6873) KateViewDocumentProxyModel::updateBackgrounds: false
kate(6873) KateApp::startupKate: KateApplication::init finished successful
kate(6873) KateViewDocumentProxyModel::updateBackgrounds: true
QThreadStorage: Thread 0x1b2d860 exited after QThreadStorage 2147483643 destroyed
scott@scottspc:~$ The file /etc/xorg.conf could not be loaded, as it was not possible to read from it.
bash: The: command not found
scott@scottspc:~$
scott@scottspc:~$ Check if you have read access to this file.

And this message poped up too.

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


And this too


The file /etc/x11/xorg.conf could not be loaded, as it was not possible to read from it.

Check if you have read access to this file.



What do I do?

Scott

---

### Post by Wicca on 2008-11-01
> **sspletttstoeszer said:**
> 
And this message poped up too.

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig")

The other problem I can't help you with, sorry.

---

