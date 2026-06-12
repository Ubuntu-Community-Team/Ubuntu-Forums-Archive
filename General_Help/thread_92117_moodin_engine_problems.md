---
title: "moodin engine problems"
date: 2005-11-18
forum: General Help
---

### Post by nikolai.m on 2005-11-18
i'm trying to install moodin engine from : [http://kde-look.org/content/show.php?content=25705](http://kde-look.org/content/show.php?content=25705) and i get folowing at "make".
please help me out here
thnx


[INDENT]make  all-recursive
make[1]: Entering directory `/home/nikolai/softs/kde-look/ksplash-engine-moodin_0.4.2/moodin'
Making all in src
make[2]: Entering directory `/home/nikolai/softs/kde-look/ksplash-engine-moodin_0.4.2/moodin/src'
if /bin/sh ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include/kde/ksplash  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wno-non-virtual-dtor -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT thememoodin.lo -MD -MP -MF ".deps/thememoodin.Tpo" \
  -c -o thememoodin.lo `test -f 'thememoodin.cpp' || echo './'`thememoodin.cpp; \
then mv -f ".deps/thememoodin.Tpo" ".deps/thememoodin.Plo"; \
else rm -f ".deps/thememoodin.Tpo"; exit 1; \
fi
In file included from thememoodin.cpp:32:
thememoodin.h:20:25: error: themeengine.h: No such file or directory
thememoodin.h:21:24: error: objkstheme.h: No such file or directory
thememoodin.h:34: error: expected class-name before '{' token
thememoodin.cpp: In constructor 'ThemeMoodin::ThemeMoodin(QWidget*, const char*, const QStringList&)':
thememoodin.cpp:38: error: class 'ThemeMoodin' does not have any field named 'ThemeEngine'
thememoodin.cpp: In member function 'void ThemeMoodin::readSettings()':
thememoodin.cpp:47: error: 'mTheme' was not declared in this scope
thememoodin.cpp: In member function 'void ThemeMoodin::init()':
thememoodin.cpp:114: error: 'NoBackground' was not declared in this scope
thememoodin.cpp:114: error: 'setBackgroundMode' was not declared in this scope
thememoodin.cpp:115: error: 'setFixedSize' was not declared in this scope
thememoodin.cpp:117: error: no matching function for call to 'QWidget::QWidget(ThemeMoodin* const)'
/usr/share/qt3/include/qwidget.h:696: note: candidates are: QWidget::QWidget(const QWidget&)
/usr/share/qt3/include/qwidget.h:135: note:                 QWidget::QWidget(QWidget*, const char*, uint)
thememoodin.cpp:118: error: 'size' was not declared in this scope
thememoodin.cpp:120: error: 'mTheme' was not declared in this scope
thememoodin.cpp:133: error: 'move' was not declared in this scope
thememoodin.cpp: In member function 'void ThemeMoodin::initBackground(QPainter*)':
thememoodin.cpp:156: error: 'mTheme' was not declared in this scope
thememoodin.cpp:160: error: 'mTheme' was not declared in this scope
thememoodin.cpp:160: error: 'width' was not declared in this scope
thememoodin.cpp:160: error: 'height' was not declared in this scope
thememoodin.cpp:163: error: 'mTheme' was not declared in this scope
thememoodin.cpp:167: error: no matching function for call to 'KMessageBox::error(ThemeMoodin* const, QString)'
/usr/include/kde/kmessagebox.h:604: note: candidates are: static void KMessageBox::error(QWidget*, const QString&, const QString&, int)
thememoodin.cpp: In member function 'void ThemeMoodin::initEffectWidgets()':
thememoodin.cpp:235: error: 'mTheme' was not declared in this scope
thememoodin.cpp: In member function 'void ThemeMoodin::arrangeWidget(QWidget*, int)':
thememoodin.cpp:270: error: 'width' was not declared in this scope
thememoodin.cpp:270: error: 'height' was not declared in this scope
thememoodin.cpp: In member function 'void ThemeMoodin::slotSetPixmap(const QString&)':
thememoodin.cpp:349: error: 'repaint' was not declared in this scope
thememoodin.moc: In static member function 'static QMetaObject* ThemeMoodin::staticMetaObject()':
thememoodin.moc:54: error: 'ThemeEngine' has not been declared
thememoodin.moc: In member function 'virtual void* ThemeMoodin::qt_cast(const char*)':
thememoodin.moc:84: error: 'ThemeEngine' has not been declared
thememoodin.moc: In member function 'virtual bool ThemeMoodin::qt_invoke(int, QUObject*)':
thememoodin.moc:93: error: 'ThemeEngine' has not been declared
thememoodin.moc: In member function 'virtual bool ThemeMoodin::qt_emit(int, QUObject*)':
thememoodin.moc:100: error: 'ThemeEngine' has not been declared
thememoodin.moc: In member function 'virtual bool ThemeMoodin::qt_property(int, int, QVariant*)':
thememoodin.moc:106: error: 'ThemeEngine' has not been declared
/usr/include/kde/kgenericfactory.h: In member function 'QObject* KGenericFactory<Product, ParentType>::createObject(QObject*, const char*, const char*, const QStringList&) [with Product = ThemeMoodin, ParentType = QObject]':
thememoodin.moc:108:   instantiated from here
/usr/include/kde/kgenericfactory.h:194: error: cannot convert 'ThemeMoodin*' to 'QObject*' in return
/usr/include/kde/kgenericfactory.tcc: In static member function 'static Product* KDEPrivate::ConcreteFactory<Product, ParentType>::create(QWidget*, const char*, QObject*, const char*, const QStringList&, KDEPrivate::Type2Type<QObject>) [with Product = ThemeMoodin, ParentType = QObject]':
/usr/include/kde/kgenericfactory.tcc:133:   instantiated from 'static Product* KDEPrivate::ConcreteFactory<Product, ParentType>::create(QWidget*, const char*, QObject*, const char*, const char*, const QStringList&) [with Product = ThemeMoodin, ParentType = QObject]'
/usr/include/kde/kgenericfactory.h:194:   instantiated from 'QObject* KGenericFactory<Product, ParentType>::createObject(QObject*, const char*, const char*, const QStringList&) [with Product = ThemeMoodin, ParentType = QObject]'
thememoodin.moc:108:   instantiated from here
/usr/include/kde/kgenericfactory.tcc:167: error: invalid conversion from 'QObject*' to 'QWidget*'
/usr/include/kde/kgenericfactory.tcc:167: error:   initializing argument 1 of 'ThemeMoodin::ThemeMoodin(QWidget*, const char*, const QStringList&)'
make[2]: *** [thememoodin.lo] Error 1
make[2]: Leaving directory `/home/nikolai/softs/kde-look/ksplash-engine-moodin_0.4.2/moodin/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nikolai/softs/kde-look/ksplash-engine-moodin_0.4.2/moodin'
make: *** [all] Error 2[/INDENT]

---

### Post by jpmontalbo on 2005-11-18
hello, did you install necessary dev packages? also, did you do:
```
./configure --prefix=/usr
```

The way I did it before compiling everything was install necessary packages.

```
sudo apt-get install build-essential kdebase-dev checkinstall
```

This will install everything that compiling programs need. :p

---

### Post by nikolai.m on 2005-11-19
thnx jpmontalbo,
kdebase-dev did it...

---

### Post by jpmontalbo on 2005-11-19
[QUOTE=nikolai.m]thnx jpmontalbo,
kdebase-dev did it...[/QUOTE]

No problem glad I can help :) . Installing those packages should also help in compiling other kde applications from source.

---

### Post by stanz on 2006-04-05
geez... kdebase-dev...comes with afew depends!? 
with kubuntu- i see most there? kate & such...I wonder if
i'm gonna brake something...or does anyone think/know,
it's all good?!!
i got checkinstall/watch & had build-essential.
**Update:** [U]Here's what i found:
[/U][I]Fading KDE splash screen engine: This KDE splash screen engine is based upon Linspire's
engine by Sean Meiners <Sean.Meiners@LinspireInc.com>
Homepage: [http://www.kde-look.org/content/show.php?content=25705](http://www.kde-look.org/content/show.php?content=25705)

[/I]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

