---
title: "[SOLVED] kontrollerlab: error while loading shared libraries"
date: 2008-09-05
forum: General Help
---

### Post by keplerspeed on 2008-09-05
Hello!

I am trying to use Kontrollerlab, so I can get back into programming my AVR butterfly microcontroller. I installed Kontrollerlab by downloading the ubuntu Dapper .deb package from here:

[http://www.cadmaniac.org/projectMain.php?projectName=kontrollerlab&section=download](http://www.cadmaniac.org/projectMain.php?projectName=kontrollerlab&section=download)

Yes i am using Hardy Heron.... Should the dapper package still work? As I have an AMD Turion64 (32 bit linux) I have to force-architecture to make it install. It installed ok, but when i type in kontrollerlab, to launch it, i get this error:

kontrollerlab: error while loading shared libraries: libktexteditor.so.0: wrong ELF class: ELFCLASS64

So it seems like I have the 64 bit libtexteditor.so.0 library?? Apparently the libtexteditor.so.0 library is in the package ia32-libs-kde but this metapackage is not still used with Hardy.

So what can I do to use Kontrollerlab?? I need it! Also I have tried compiling the source, ./configure runs fine, but then make stalls, well, the cpu is still banging away but the last line of code in the terminal stops, and it says:

/usr/include/kde/ktexteditor/cursorinterface.h:34: warning: ‘class KTextEditor::Cursor’ has virtual functions but non-virtual destructor

and its just blank under that, no lines of stuff, just a wizzing fan and lots of hot air.... the process cc1plus is doing something.... 94% cpu by typing in "top" to the terminal.

cheers

---

### Post by keplerspeed on 2008-09-06
I was just being impatient, after leaving the source to compile, yes it takes ages, it worked! So the solution, is to compile the source code, and be patient.

---

