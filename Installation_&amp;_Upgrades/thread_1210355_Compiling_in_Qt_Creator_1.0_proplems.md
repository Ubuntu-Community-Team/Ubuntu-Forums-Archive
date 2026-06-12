---
title: "Compiling in Qt Creator 1.0 proplems"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by msbealo on 2009-07-11
Hi,

I'm having problems compiling simple programs in QT Creator, this happens when I try to compile a virgin mainwindow, and also on the installed Qt demo "chip".

I copy the "chip" demo into my home directory and try to compile. I get this error message:

```
Running build steps for project chip...
Creating gdb macros library...
Starting: /usr/bin/qmake-qt4 /home/msbealo/Qt/chip/chip.pro -spec /usr/share/qt4/mkspecs/linux-g++ -r CONFIG+=debug_and_release CONFIG+=debug 
Exited with code 0.
Starting: /usr/bin/make debug -w 
make: Entering directory `/home/msbealo/Qt/chip'
/usr/bin/make -f Makefile.Debug
make[1]: Entering directory `/home/msbealo/Qt/chip'
g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4 -I/usr/X11R6/include -Idebug -I. -o debug/main.o main.cpp
make[1]: g++: Command not found
make[1]: *** [debug/main.o] Error 127
make[1]: Leaving directory `/home/msbealo/Qt/chip'
make: Leaving directory `/home/msbealo/Qt/chip'
make: *** [debug] Error 2
Exited with code 2.
Error while building project chip
When executing build step 'Make'
```

However, if I compile using the terminal by just typing:

```
qmake chip.pro
make
```

then it compile successfully. 

I'm quite new to this, so please keep it simple.

I'm running 9.04 on a 64 bit core i7 920 using the qt-creator 1.0.0-ubuntu3 package from Synaptic.

Mark

---

### Post by hakermania on 2010-01-29
same problem with 32 bit system....:( mine....No answer as I can see...:( I tried to reintsall several times the Qt creator but:(

---

