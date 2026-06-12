---
title: "Using OpenGL with C++ (make)"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by RedNifre on 2008-12-05
Hello,

I'm trying to compile a c++ project that uses GTK and OpenGL. It runs on other Linux Systems so I guess my Ubuntu 8.04 is missing something.

When I run "make" I get these errors:
```

Package gtkglextmm-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkglextmm-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkglextmm-1.2' found
Package gtkglextmm-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkglextmm-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkglextmm-1.2' found
g++ -Wall -g  -c main.cc -o main.o
main.cc:3:19: Fehler: gtkmm.h: No such file or directory
main.cc:4:21: Fehler: gtkglmm.h: No such file or directory
main.cc:6:19: Fehler: GL/gl.h: No such file or directory
In Datei, eingefügt von view.h:5,
                 von application.h:5,
                 von main.cc:8:
scene.h:9:20: Fehler: GL/glu.h: No such file or directory
In file included from view.h:5,
                 from application.h:5,
                 from main.cc:8:
scene.h:85: Fehler: »GLuint« bezeichnet keinen Typ
In file included from application.h:5,
                 from main.cc:8:
view.h:10: Fehler: »Gtk« wurde nicht deklariert
view.h:10: Fehler: expected `{' before »DrawingArea«
view.h:10: Fehler: Funktionsdefinition deklariert keine Parameter
In file included from main.cc:8:
application.h:9: Fehler: »Gtk« wurde nicht deklariert
application.h:9: Fehler: expected `{' before »Window«
application.h:9: Fehler: Funktionsdefinition deklariert keine Parameter
main.cc: In function »int main(int, char**)«:
main.cc:13: Fehler: »Gtk« wurde nicht deklariert
main.cc:13: Fehler: expected `;' before »kit«
main.cc:16: Fehler: »Gtk« wurde nicht deklariert
main.cc:18: Fehler: Aggregat »Application app« hat unvollständigen Typ und kann nicht definiert werden
main.cc:19: Fehler: »Gtk« wurde nicht deklariert
make: *** [main.o] Fehler 1

```

I don't understand the error message. What should I do?
I also have something that looks like the OpenGL extension:

```
 
sudo find / -name 'gtkgl*'

/usr/lib/python2.5/site-packages/gtk-2.0/gtk/gtkgl
/usr/lib/python2.4/site-packages/gtk-2.0/gtk/gtkgl
/usr/lib/python-support/python-gtkglext1/python2.5/gtk-2.0/gtk/gtkgl
/usr/lib/python-support/python-gtkglext1/python2.4/gtk-2.0/gtk/gtkgl
/usr/share/pygtk/2.0/defs/gtkglext.defs
/usr/share/python-support/python-gtkglext1/gtk-2.0/gtk/gtkgl
/var/lib/python-support/python2.5/gtk-2.0/gtk/gtkgl
/var/lib/python-support/python2.4/gtk-2.0/gtk/gtkgl

```

But it seems to be for python, while my project is written in C++.
What should I do to compile my project?

(I'm a Linux newbie; I would appreciate a fool-proof answer ;-)

---

### Post by RedNifre on 2008-12-05
I just found out that I can run "glxgears" and see some nice spinning gears. So I guess my ubuntu can do OpenGL. Why does "make" fail? What should I do? :-(

---

### Post by regala on 2008-12-05
> **RedNifre said:**
> I just found out that I can run "glxgears" and see some nice spinning gears. So I guess my ubuntu can do OpenGL. Why does "make" fail? What should I do? :-(

When you want to build something, you usually need development files along the library files, like headers (hint: gtkmm.h is not on your system, how can gcc find it ?)

then you go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and in the forms in the bottom of the page, you find that you, **_at least_**, need to install *libgtkmm-2.4-dev*. Maybe you will need more, but there's a chance that dependencies will take care of all what you need.

cheers

---

