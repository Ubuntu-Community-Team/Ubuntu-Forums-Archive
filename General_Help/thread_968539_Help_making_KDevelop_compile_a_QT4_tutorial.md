---
title: "Help making KDevelop compile a QT4 tutorial"
date: 2008-11-02
forum: General Help
---

### Post by Sivar on 2008-11-02
I'm trying to get KDevelop to compile a QT4 app -- ANY QT4 app, but it just absolutely will not do it.

I have everything I need installed (qt4-dev-tools, build-essential, etc).

QT3 is not installed. I know QT4 development works because I can make PyQT4 apps (QT in Python)

---
I open KDevelop, make a new project, Qmake, "Basic QT4 application". It inserts code to print "Hello, World!" in the console. That works fine.

I can also make a more advanced "QT4 application", which makes a whole QT4 text editor. That works fine.

The problem is, if I try to make my own code, or paste in any tutorial code, I get errors compiling. I am starting with "Basic QT4 application."


This is my code, from a TrollTech QT4 tutorial:

```

#include <QApplication>
#include <QFont>
#include <QPushButton>

int main(int argc, char *argv[])
{
	QApplication app(argc, argv);
	QPushButton quit("Quit");
	quit.resize(75, 30);
	quit.setFont(QFont("Times", 18, QFont::Bold));
	QObject::connect(&quit, SIGNAL(clicked()), &app, SLOT(quit()));
	quit.show();
	return app.exec();
}
```

When I compile, I get these (and more) errors. Note the last error.

```
cd '/home/charles/projects/battlezone/trunk' && LC_MESSAGES="C" LC_CTYPE="C" make -k 
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o main.o src/main.cpp
src/main.cpp: In function 'int main(int, char**)':
src/main.cpp:24: error: 'QApplication' was not declared in this scope.

```

This happens whether I use KDevelop's build buttons or QMake Manager's. It happens even if I go to the command line and type:

Please let me know how I can get a C++ KDevelop project to compile!
I'd sure like to use QT because it's multi-platform and much easier to use than GTK+ or, especially, the Win32 API (for Windows), but it sure is frustrating when an editor written in QT, for a desktop environment written in QT, can't compile a QT application.

---

### Post by sonofusion82 on 2008-11-02
i don't have my kubuntu machine with kdevelop right now, i remember i has to change some project settings.
If you can compile the "QT4 application", then Qt4 is working, perhaps you can compare the project setting between that and yours.
If I am not mistaken, there is somewhere that you need to enable the Qt4 libraries to be included/linked with the build.
This is a common problem with IDEs include Visual Studio, so many project settings hidden under so many menus to just enable something to built properly.

---

