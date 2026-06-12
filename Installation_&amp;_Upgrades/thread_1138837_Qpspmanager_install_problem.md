---
title: "Qpspmanager install problem"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by nathand28 on 2009-04-26
When trying to install Qpspmanager with [these]("https://help.ubuntu.com/community/PSP") instructions, when I run qmake in the pspmanager directory, I get these warnings:
```
WARNING: Found potential symbol conflict of mainwindow.cpp (src/mainwindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of mainwindow.h (src/mainwindow.h) in HEADERS
WARNING: Found potential symbol conflict of optionswidget.cpp (src/optionswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of optionswidget.h (src/optionswidget.h) in HEADERS
WARNING: Found potential symbol conflict of videoswidget.cpp (src/videoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of videoswidget.h (src/videoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of applicationswidget.cpp (src/applicationswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of applicationswidget.h (src/applicationswidget.h) in HEADERS
WARNING: Found potential symbol conflict of backupswidget.cpp (src/backupswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of backupswidget.h (src/backupswidget.h) in HEADERS
WARNING: Found potential symbol conflict of isoswidget.cpp (src/isoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of isoswidget.h (src/isoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of helpwidget.cpp (src/helpwidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of helpwidget.h (src/helpwidget.h) in HEADERS
WARNING: Found potential symbol conflict of mainwindow.cpp (src/mainwindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of mainwindow.h (src/mainwindow.h) in HEADERS
WARNING: Found potential symbol conflict of optionswidget.cpp (src/optionswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of optionswidget.h (src/optionswidget.h) in HEADERS
WARNING: Found potential symbol conflict of videoswidget.cpp (src/videoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of videoswidget.h (src/videoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of applicationswidget.cpp (src/applicationswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of applicationswidget.h (src/applicationswidget.h) in HEADERS
WARNING: Found potential symbol conflict of backupswidget.cpp (src/backupswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of backupswidget.h (src/backupswidget.h) in HEADERS
WARNING: Found potential symbol conflict of isoswidget.cpp (src/isoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of isoswidget.h (src/isoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of helpwidget.cpp (src/helpwidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of helpwidget.h (src/helpwidget.h) in HEADERS
```
And when I run make:
```
uic: File generated with too recent version of Qt Designer (4.0 vs. 3.3.8b)
make: *** [ui/isoswidget.h] Error 1
```
At the end of a lot of errors.
I have tried uninstalling libqtcore4 and libqtgui4 and that didn't work. Also, I removed qt4-designer and installed qt3-designer from [http://linuxappfinder.com/package/qt3-designer](http://linuxappfinder.com/package/qt3-designer) but still it didn't work.
I have installed everything needed for the official manager, and runs when I click the .desktop file, but only goes to a dialogue box or something like that.  
I am running Ubuntu 9.04, if that matters.

---

### Post by nathand28 on 2009-04-28
I fixed it with:
```
sudo apt-get remove qt3-dev-tools libqt3-mt-dev
sudo apt-get install libqt4-dev
```
From [this]("http://ubuntuforums.org/showthread.php?t=569573") thread.
But, still, how do I run Sony Media manager?

---

### Post by bskumar7080 on 2010-09-07
Thank You [nathand28]("http://newyork.ubuntuforums.org/member.php?u=675109") , i was able to fix the problem

---

