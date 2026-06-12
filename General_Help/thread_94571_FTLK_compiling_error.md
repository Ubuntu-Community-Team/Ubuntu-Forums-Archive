---
title: "FTLK compiling error"
date: 2005-11-24
forum: General Help
---

### Post by commodore on 2005-11-24
I was compiling FLTK and got this error:
I have to compile fltk 1.0. I'm not allowed to compile 1.1. But I can't do that. I get this error:
=== making src ===
make[1]: Entering directory `/home/nummer/src/fltk/src'
Compiling Fl.o...
../FL/Fl_Window.H:35: error: ISO C++ forbids declaration of ‘Fl_X’ with no type
../FL/Fl_Window.H:35: error: expected ‘;’ before ‘*’ token
../FL/Fl_Window.H: In member function ‘int Fl_Window::shown()’:
../FL/Fl_Window.H:93: error: ‘i’ was not declared in this scope
../FL/x.H: In static member function ‘static Fl_X* Fl_X::i(const Fl_Window*)’:
../FL/x.H:106: error: ‘const class Fl_Window’ has no member named ‘i’
../FL/x.H: In member function ‘void Fl_X::setwindow(Fl_Window*)’:
../FL/x.H:107: error: ‘class Fl_Window’ has no member named ‘i’
Fl.cxx: In member function ‘virtual void Fl_Window::hide()’:
Fl.cxx:611: error: ‘i’ was not declared in this scope
Fl.cxx: In member function ‘virtual void Fl_Window::flush()’:
Fl.cxx:778: error: ‘i’ was not declared in this scope
make[1]: *** [Fl.o] Error 1
make[1]: Leaving directory `/home/nummer/src/fltk/src'

I must compile 1.0, I can't use anything never or older.

---

### Post by commodore on 2005-11-25
Atleast say it's impossible then I'm not watching this thread anymore.

---

