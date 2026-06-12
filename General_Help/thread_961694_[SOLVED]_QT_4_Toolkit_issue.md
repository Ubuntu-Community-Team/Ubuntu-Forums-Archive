---
title: "[SOLVED] QT 4 Toolkit issue"
date: 2008-10-28
forum: General Help
---

### Post by metalmaniac248 on 2008-10-28
i download the QT4 toolkit sources, and when i run ./configure i get this output, there seems to be an error, and it is stopping me from compiling the sources, and installing the program,

this is the output

> This is the Qt/X11 Open Source Edition.

basename: extra operand `Place/qt-x11-opensource-src-4.4.3/src/plugins/sqldrivers/ibase'
Try `basename --help' for more information.
basename: extra operand `Place/qt-x11-opensource-src-4.4.3/src/plugins/sqldrivers/mysql'
Try `basename --help' for more information.
basename: extra operand `Place/qt-x11-opensource-src-4.4.3/src/plugins/sqldrivers/odbc'
Try `basename --help' for more information.
basename: extra operand `Place/qt-x11-opensource-src-4.4.3/src/plugins/sqldrivers/psql'
Try `basename --help' for more information.
basename: extra operand `Place/qt-x11-opensource-src-4.4.3/src/plugins/sqldrivers/sqlite'
Try `basename --help' for more information.
basename: extra operand `Place/qt-x11-opensource-src-4.4.3/src/plugins/sqldrivers/sqlite2'
Try `basename --help' for more information.
./configure: 1935: /media/My: not found
You don't seem to have 'make' or 'gmake' in your PATH.
Cannot proceed.


any ideas?






thanks

---

### Post by snova on 2008-10-28
It appears to be a bug in the Qt configure script. I suspect that it is because there is a space in the installation path you specified, or possibly in $PATH.

Where are you trying to install it to?

---

### Post by metalmaniac248 on 2008-10-28
i just cd to the qt folder , which is on my external hdd, then i run ./configure

---

### Post by snova on 2008-10-28
Try running it from somewhere without a space in the name, like your home directory.

Spaces can do weird things to shell scripts. It's probably trying to figure out where it is, or something like that.

---

### Post by metalmaniac248 on 2008-10-29
thanks i managed to complete the installation,

does anyone know how to actually run it as i cant seem to find the command

---

### Post by snova on 2008-10-29
What do you mean? Qt is a library, not a program. There's nothing to run.

And why were you building it in the first place? (Should have asked that earlier...) Unless you need a really up-to-date version, it's in the repositories...

---

### Post by metalmaniac248 on 2008-10-29
sorry it appears i am a bit confused :lolflag:




thanks anyway

---

