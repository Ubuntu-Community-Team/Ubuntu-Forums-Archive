---
title: "Trying To Install Obpager. Error After Error, After Error, After Error"
date: 2008-09-22
forum: General Help
---

### Post by Mark76 on 2008-09-22
I'm beginning to suspect the stupid program wasn't even written for Linux/unix ](*,)

> ~/obpager-1.8$ make
Compiling src/main.cc
In file included from src/main.cc:33:
src/OBPager.h:33:18: warning: Xlib.h: No such file or directory
src/OBPager.h:34:19: warning: Xutil.h: No such file or directory
src/OBPager.h:35:17: warning: Xos.h: No such file or directory
src/OBPager.h:36:19: warning: Xatom.h: No such file or directory
src/OBPager.h:37:19: warning: shape.h: No such file or directory
In file included from src/OBPager.h:42,
                 from src/main.cc:33:
src/XHelperClasses.h:181: error: expected `)' before '*' token
src/XHelperClasses.h:197: error: 'Display' has not been declared
src/XHelperClasses.h:229: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:229: error: expected ';' before '*' token
src/XHelperClasses.h:236: error: expected `;' before 'Display'
src/XHelperClasses.h:236: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:236: error: expected ';' before '*' token
src/XHelperClasses.h:242: error: expected `;' before 'private'
src/XHelperClasses.h:253: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:253: error: expected ';' before '*' token
src/XHelperClasses.h: In constructor 'XDisplayKeeper::XDisplayKeeper()':
src/XHelperClasses.h:173: error: class 'XDisplayKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h: In member function 'void XDisplayKeeper::acquire(int*)':
src/XHelperClasses.h:201: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h: In member function 'void XDisplayKeeper::release()':
src/XHelperClasses.h:213: error: 'Display' was not declared in this scope
src/XHelperClasses.h:213: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:213: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:222: error: 'XCloseDisplay' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:281: error: expected `)' before '*' token
src/XHelperClasses.h:297: error: 'Display' has not been declared
src/XHelperClasses.h:297: error: 'Window' has not been declared
src/XHelperClasses.h:332: error: 'Window' does not name a type
src/XHelperClasses.h:339: error: ISO C++ forbids declaration of 'Window' with no type
src/XHelperClasses.h:339: error: expected ';' before 'operator'
src/XHelperClasses.h:345: error: expected `;' before 'private'
src/XHelperClasses.h:354: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:354: error: expected ';' before '*' token
src/XHelperClasses.h:357: error: 'Window' does not name a type
src/XHelperClasses.h: In constructor 'XWindowKeeper::XWindowKeeper()':
src/XHelperClasses.h:273: error: class 'XWindowKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:273: error: class 'XWindowKeeper' does not have any field named 'mWindow'
src/XHelperClasses.h: In member function 'void XWindowKeeper::acquire(int*, int)':
src/XHelperClasses.h:301: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:302: error: 'mWindow' was not declared in this scope
src/XHelperClasses.h: In member function 'void XWindowKeeper::release()':
src/XHelperClasses.h:314: error: 'Display' was not declared in this scope
src/XHelperClasses.h:314: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:314: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:315: error: 'Window' was not declared in this scope
src/XHelperClasses.h:315: error: expected `;' before 'oldWindow'
src/XHelperClasses.h:318: error: 'mWindow' was not declared in this scope
src/XHelperClasses.h:320: error: 'oldWindow' was not declared in this scope
src/XHelperClasses.h:325: error: 'XDestroyWindow' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:385: error: expected `)' before '*' token
src/XHelperClasses.h:401: error: 'Display' has not been declared
src/XHelperClasses.h:401: error: 'XFontStruct' has not been declared
src/XHelperClasses.h:436: error: ISO C++ forbids declaration of 'XFontStruct' with no type
src/XHelperClasses.h:436: error: expected ';' before '*' token
src/XHelperClasses.h:444: error: expected `;' before 'XFontStruct'
src/XHelperClasses.h:444: error: ISO C++ forbids declaration of 'XFontStruct' with no type
src/XHelperClasses.h:444: error: expected ';' before '*' token
src/XHelperClasses.h:450: error: expected `;' before 'private'
src/XHelperClasses.h:461: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:461: error: expected ';' before '*' token
src/XHelperClasses.h:465: error: ISO C++ forbids declaration of 'XFontStruct' with no type
src/XHelperClasses.h:465: error: expected ';' before '*' token
src/XHelperClasses.h: In constructor 'XFontStructKeeper::XFontStructKeeper()':
src/XHelperClasses.h:377: error: class 'XFontStructKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:377: error: class 'XFontStructKeeper' does not have any field named 'mFontStruct'
src/XHelperClasses.h: In member function 'void XFontStructKeeper::acquire(int*, int*)':
src/XHelperClasses.h:405: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:406: error: 'mFontStruct' was not declared in this scope
src/XHelperClasses.h: In member function 'void XFontStructKeeper::release()':
src/XHelperClasses.h:418: error: 'Display' was not declared in this scope
src/XHelperClasses.h:418: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:418: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:419: error: 'XFontStruct' was not declared in this scope
src/XHelperClasses.h:419: error: 'oldFontStruct' was not declared in this scope
src/XHelperClasses.h:419: error: 'mFontStruct' was not declared in this scope
src/XHelperClasses.h:429: error: 'XFreeFont' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:493: error: expected `)' before '*' token
src/XHelperClasses.h:509: error: 'Display' has not been declared
src/XHelperClasses.h:509: error: 'GC' has not been declared
src/XHelperClasses.h:544: error: 'GC' does not name a type
src/XHelperClasses.h:552: error: ISO C++ forbids declaration of 'GC' with no type
src/XHelperClasses.h:552: error: expected ';' before 'operator'
src/XHelperClasses.h:558: error: expected `;' before 'private'
src/XHelperClasses.h:569: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:569: error: expected ';' before '*' token
src/XHelperClasses.h:574: error: 'GC' does not name a type
src/XHelperClasses.h: In constructor 'XGCKeeper::XGCKeeper()':
src/XHelperClasses.h:485: error: class 'XGCKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:485: error: class 'XGCKeeper' does not have any field named 'mGC'
src/XHelperClasses.h: In member function 'void XGCKeeper::acquire(int*, int)':
src/XHelperClasses.h:513: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:514: error: 'mGC' was not declared in this scope
src/XHelperClasses.h: In member function 'void XGCKeeper::release()':
src/XHelperClasses.h:526: error: 'Display' was not declared in this scope
src/XHelperClasses.h:526: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:526: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:527: error: 'GC' was not declared in this scope
src/XHelperClasses.h:527: error: expected `;' before 'oldGC'
src/XHelperClasses.h:530: error: 'mGC' was not declared in this scope
src/XHelperClasses.h:532: error: 'oldGC' was not declared in this scope
src/XHelperClasses.h:537: error: 'XFreeGC' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:602: error: expected `)' before '*' token
src/XHelperClasses.h:618: error: 'Display' has not been declared
src/XHelperClasses.h:618: error: 'Pixmap' has not been declared
src/XHelperClasses.h:653: error: 'Pixmap' does not name a type
src/XHelperClasses.h:661: error: ISO C++ forbids declaration of 'Pixmap' with no type
src/XHelperClasses.h:661: error: expected ';' before 'operator'
src/XHelperClasses.h:667: error: expected `;' before 'private'
src/XHelperClasses.h:678: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:678: error: expected ';' before '*' token
src/XHelperClasses.h:683: error: 'Pixmap' does not name a type
src/XHelperClasses.h: In constructor 'XPixmapKeeper::XPixmapKeeper()':
src/XHelperClasses.h:594: error: class 'XPixmapKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:594: error: class 'XPixmapKeeper' does not have any field named 'mPixmap'
src/XHelperClasses.h: In member function 'void XPixmapKeeper::acquire(int*, int)':
src/XHelperClasses.h:622: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:623: error: 'mPixmap' was not declared in this scope
src/XHelperClasses.h: In member function 'void XPixmapKeeper::release()':
src/XHelperClasses.h:635: error: 'Display' was not declared in this scope
src/XHelperClasses.h:635: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:635: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:636: error: 'Pixmap' was not declared in this scope
src/XHelperClasses.h:636: error: expected `;' before 'oldPixmap'
src/XHelperClasses.h:639: error: 'mPixmap' was not declared in this scope
src/XHelperClasses.h:641: error: 'oldPixmap' was not declared in this scope
src/XHelperClasses.h:646: error: 'XFreePixmap' was not declared in this scope
In file included from src/main.cc:33:
src/OBPager.h: At global scope:
src/OBPager.h:81: error: 'Display' has not been declared
src/OBPager.h:81: error: 'XErrorEvent' has not been declared
src/OBPager.h:90: error: 'Window' has not been declared
src/OBPager.h:93: error: 'Atom' has not been declared
src/OBPager.h:93: error: 'Atom' has not been declared
src/OBPager.h:93: error: 'Window' has not been declared
src/OBPager.h:96: error: 'Atom' has not been declared
src/OBPager.h:96: error: 'Atom' has not been declared
src/OBPager.h:96: error: 'Window' has not been declared
src/OBPager.h:99: error: 'Atom' has not been declared
src/OBPager.h:99: error: 'Atom' has not been declared
src/OBPager.h:99: error: 'Window' has not been declared
src/OBPager.h:109: error: expected ',' or '...' before 'colorMap'
src/OBPager.h:109: error: ISO C++ forbids declaration of 'Colormap' with no type
src/OBPager.h:162: error: 'Atom' does not name a type
src/OBPager.h:163: error: 'Atom' does not name a type
src/OBPager.h:164: error: 'Atom' does not name a type
src/OBPager.h:165: error: 'Atom' does not name a type
src/OBPager.h:166: error: 'Atom' does not name a type
src/OBPager.h:167: error: 'Atom' does not name a type
src/OBPager.h:168: error: 'Atom' does not name a type
src/OBPager.h:169: error: 'Atom' does not name a type
src/OBPager.h:170: error: 'Atom' does not name a type
src/OBPager.h:171: error: 'Atom' does not name a type
src/OBPager.h:172: error: 'Atom' does not name a type
src/OBPager.h:93: error: 'XA_CARDINAL' was not declared in this scope
src/OBPager.h:96: error: 'XA_CARDINAL' was not declared in this scope
src/OBPager.h:99: error: 'XA_STRING' was not declared in this scope
src/main.cc: In function 'int main(int, char**)':
src/main.cc:161: error: 'errno' was not declared in this scope
src/main.cc:194: error: 'errno' was not declared in this scope
Compiling src/OBPager.cc
In file included from src/OBPager.cc:20:
src/OBPager.h:33:18: warning: Xlib.h: No such file or directory
src/OBPager.h:34:19: warning: Xutil.h: No such file or directory
src/OBPager.h:35:17: warning: Xos.h: No such file or directory
src/OBPager.h:36:19: warning: Xatom.h: No such file or directory
src/OBPager.h:37:19: warning: shape.h: No such file or directory
In file included from src/OBPager.h:42,
                 from src/OBPager.cc:20:
src/XHelperClasses.h:181: error: expected `)' before '*' token
src/XHelperClasses.h:197: error: 'Display' has not been declared
src/XHelperClasses.h:229: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:229: error: expected ';' before '*' token
src/XHelperClasses.h:236: error: expected `;' before 'Display'
src/XHelperClasses.h:236: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:236: error: expected ';' before '*' token
src/XHelperClasses.h:242: error: expected `;' before 'private'
src/XHelperClasses.h:253: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:253: error: expected ';' before '*' token
src/XHelperClasses.h: In constructor 'XDisplayKeeper::XDisplayKeeper()':
src/XHelperClasses.h:173: error: class 'XDisplayKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h: In member function 'void XDisplayKeeper::acquire(int*)':
src/XHelperClasses.h:201: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h: In member function 'void XDisplayKeeper::release()':
src/XHelperClasses.h:213: error: 'Display' was not declared in this scope
src/XHelperClasses.h:213: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:213: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:222: error: 'XCloseDisplay' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:281: error: expected `)' before '*' token
src/XHelperClasses.h:297: error: 'Display' has not been declared
src/XHelperClasses.h:297: error: 'Window' has not been declared
src/XHelperClasses.h:332: error: 'Window' does not name a type
src/XHelperClasses.h:339: error: ISO C++ forbids declaration of 'Window' with no type
src/XHelperClasses.h:339: error: expected ';' before 'operator'
src/XHelperClasses.h:345: error: expected `;' before 'private'
src/XHelperClasses.h:354: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:354: error: expected ';' before '*' token
src/XHelperClasses.h:357: error: 'Window' does not name a type
src/XHelperClasses.h: In constructor 'XWindowKeeper::XWindowKeeper()':
src/XHelperClasses.h:273: error: class 'XWindowKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:273: error: class 'XWindowKeeper' does not have any field named 'mWindow'
src/XHelperClasses.h: In member function 'void XWindowKeeper::acquire(int*, int)':
src/XHelperClasses.h:301: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:302: error: 'mWindow' was not declared in this scope
src/XHelperClasses.h: In member function 'void XWindowKeeper::release()':
src/XHelperClasses.h:314: error: 'Display' was not declared in this scope
src/XHelperClasses.h:314: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:314: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:315: error: 'Window' was not declared in this scope
src/XHelperClasses.h:315: error: expected `;' before 'oldWindow'
src/XHelperClasses.h:318: error: 'mWindow' was not declared in this scope
src/XHelperClasses.h:320: error: 'oldWindow' was not declared in this scope
src/XHelperClasses.h:325: error: 'XDestroyWindow' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:385: error: expected `)' before '*' token
src/XHelperClasses.h:401: error: 'Display' has not been declared
src/XHelperClasses.h:401: error: 'XFontStruct' has not been declared
src/XHelperClasses.h:436: error: ISO C++ forbids declaration of 'XFontStruct' with no type
src/XHelperClasses.h:436: error: expected ';' before '*' token
src/XHelperClasses.h:444: error: expected `;' before 'XFontStruct'
src/XHelperClasses.h:444: error: ISO C++ forbids declaration of 'XFontStruct' with no type
src/XHelperClasses.h:444: error: expected ';' before '*' token
src/XHelperClasses.h:450: error: expected `;' before 'private'
src/XHelperClasses.h:461: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:461: error: expected ';' before '*' token
src/XHelperClasses.h:465: error: ISO C++ forbids declaration of 'XFontStruct' with no type
src/XHelperClasses.h:465: error: expected ';' before '*' token
src/XHelperClasses.h: In constructor 'XFontStructKeeper::XFontStructKeeper()':
src/XHelperClasses.h:377: error: class 'XFontStructKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:377: error: class 'XFontStructKeeper' does not have any field named 'mFontStruct'
src/XHelperClasses.h: In member function 'void XFontStructKeeper::acquire(int*, int*)':
src/XHelperClasses.h:405: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:406: error: 'mFontStruct' was not declared in this scope
src/XHelperClasses.h: In member function 'void XFontStructKeeper::release()':
src/XHelperClasses.h:418: error: 'Display' was not declared in this scope
src/XHelperClasses.h:418: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:418: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:419: error: 'XFontStruct' was not declared in this scope
src/XHelperClasses.h:419: error: 'oldFontStruct' was not declared in this scope
src/XHelperClasses.h:419: error: 'mFontStruct' was not declared in this scope
src/XHelperClasses.h:429: error: 'XFreeFont' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:493: error: expected `)' before '*' token
src/XHelperClasses.h:509: error: 'Display' has not been declared
src/XHelperClasses.h:509: error: 'GC' has not been declared
src/XHelperClasses.h:544: error: 'GC' does not name a type
src/XHelperClasses.h:552: error: ISO C++ forbids declaration of 'GC' with no type
src/XHelperClasses.h:552: error: expected ';' before 'operator'
src/XHelperClasses.h:558: error: expected `;' before 'private'
src/XHelperClasses.h:569: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:569: error: expected ';' before '*' token
src/XHelperClasses.h:574: error: 'GC' does not name a type
src/XHelperClasses.h: In constructor 'XGCKeeper::XGCKeeper()':
src/XHelperClasses.h:485: error: class 'XGCKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:485: error: class 'XGCKeeper' does not have any field named 'mGC'
src/XHelperClasses.h: In member function 'void XGCKeeper::acquire(int*, int)':
src/XHelperClasses.h:513: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:514: error: 'mGC' was not declared in this scope
src/XHelperClasses.h: In member function 'void XGCKeeper::release()':
src/XHelperClasses.h:526: error: 'Display' was not declared in this scope
src/XHelperClasses.h:526: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:526: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:527: error: 'GC' was not declared in this scope
src/XHelperClasses.h:527: error: expected `;' before 'oldGC'
src/XHelperClasses.h:530: error: 'mGC' was not declared in this scope
src/XHelperClasses.h:532: error: 'oldGC' was not declared in this scope
src/XHelperClasses.h:537: error: 'XFreeGC' was not declared in this scope
src/XHelperClasses.h: At global scope:
src/XHelperClasses.h:602: error: expected `)' before '*' token
src/XHelperClasses.h:618: error: 'Display' has not been declared
src/XHelperClasses.h:618: error: 'Pixmap' has not been declared
src/XHelperClasses.h:653: error: 'Pixmap' does not name a type
src/XHelperClasses.h:661: error: ISO C++ forbids declaration of 'Pixmap' with no type
src/XHelperClasses.h:661: error: expected ';' before 'operator'
src/XHelperClasses.h:667: error: expected `;' before 'private'
src/XHelperClasses.h:678: error: ISO C++ forbids declaration of 'Display' with no type
src/XHelperClasses.h:678: error: expected ';' before '*' token
src/XHelperClasses.h:683: error: 'Pixmap' does not name a type
src/XHelperClasses.h: In constructor 'XPixmapKeeper::XPixmapKeeper()':
src/XHelperClasses.h:594: error: class 'XPixmapKeeper' does not have any field named 'mDisplay'
src/XHelperClasses.h:594: error: class 'XPixmapKeeper' does not have any field named 'mPixmap'
src/XHelperClasses.h: In member function 'void XPixmapKeeper::acquire(int*, int)':
src/XHelperClasses.h:622: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:623: error: 'mPixmap' was not declared in this scope
src/XHelperClasses.h: In member function 'void XPixmapKeeper::release()':
src/XHelperClasses.h:635: error: 'Display' was not declared in this scope
src/XHelperClasses.h:635: error: 'oldDisplay' was not declared in this scope
src/XHelperClasses.h:635: error: 'mDisplay' was not declared in this scope
src/XHelperClasses.h:636: error: 'Pixmap' was not declared in this scope
src/XHelperClasses.h:636: error: expected `;' before 'oldPixmap'
src/XHelperClasses.h:639: error: 'mPixmap' was not declared in this scope
src/XHelperClasses.h:641: error: 'oldPixmap' was not declared in this scope
src/XHelperClasses.h:646: error: 'XFreePixmap' was not declared in this scope
In file included from src/OBPager.cc:20:
src/OBPager.h: At global scope:
src/OBPager.h:81: error: 'Display' has not been declared
src/OBPager.h:81: error: 'XErrorEvent' has not been declared
src/OBPager.h:90: error: 'Window' has not been declared
src/OBPager.h:93: error: 'Atom' has not been declared
src/OBPager.h:93: error: 'Atom' has not been declared
src/OBPager.h:93: error: 'Window' has not been declared
src/OBPager.h:96: error: 'Atom' has not been declared
src/OBPager.h:96: error: 'Atom' has not been declared
src/OBPager.h:96: error: 'Window' has not been declared
src/OBPager.h:99: error: 'Atom' has not been declared
src/OBPager.h:99: error: 'Atom' has not been declared
src/OBPager.h:99: error: 'Window' has not been declared
src/OBPager.h:109: error: expected ',' or '...' before 'colorMap'
src/OBPager.h:109: error: ISO C++ forbids declaration of 'Colormap' with no type
src/OBPager.h:162: error: 'Atom' does not name a type
src/OBPager.h:163: error: 'Atom' does not name a type
src/OBPager.h:164: error: 'Atom' does not name a type
src/OBPager.h:165: error: 'Atom' does not name a type
src/OBPager.h:166: error: 'Atom' does not name a type
src/OBPager.h:167: error: 'Atom' does not name a type
src/OBPager.h:168: error: 'Atom' does not name a type
src/OBPager.h:169: error: 'Atom' does not name a type
src/OBPager.h:170: error: 'Atom' does not name a type
src/OBPager.h:171: error: 'Atom' does not name a type
src/OBPager.h:172: error: 'Atom' does not name a type
src/OBPager.h:93: error: 'XA_CARDINAL' was not declared in this scope
src/OBPager.h:96: error: 'XA_CARDINAL' was not declared in this scope
src/OBPager.h:99: error: 'XA_STRING' was not declared in this scope
src/OBPager.cc:71: error: 'int OBPager::errorHandler' is not a static member of 'class OBPager'
src/OBPager.cc:71: error: 'Display' was not declared in this scope
src/OBPager.cc:71: error: 'display' was not declared in this scope
src/OBPager.cc:71: error: 'XErrorEvent' was not declared in this scope
src/OBPager.cc:71: error: 'errEvent' was not declared in this scope
src/OBPager.cc:71: error: initializer expression list treated as compound expression
src/OBPager.cc:72: error: expected ',' or ';' before '{' token
src/OBPager.cc:99: error: 'Window' has not been declared
src/OBPager.cc: In member function 'void OBPager::connectToXServer(char*)':
src/OBPager.cc:171: warning: deprecated conversion from string constant to 'char*'
src/OBPager.cc:177: error: 'XSetErrorHandler' was not declared in this scope
src/OBPager.cc:185: error: 'XOpenDisplay' was not declared in this scope
src/OBPager.cc:187: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:201: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:201: error: 'XSynchronize' was not declared in this scope
src/OBPager.cc:207: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:207: error: 'DefaultScreen' was not declared in this scope
src/OBPager.cc:215: error: 'mAtom_UTF8_STRING' was not declared in this scope
src/OBPager.cc:215: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:215: error: 'True' was not declared in this scope
src/OBPager.cc:215: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:215: error: 'None' was not declared in this scope
src/OBPager.cc:219: error: 'mAtom_NET_CURRENT_DESKTOP' was not declared in this scope
src/OBPager.cc:219: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:219: error: 'True' was not declared in this scope
src/OBPager.cc:219: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:219: error: 'None' was not declared in this scope
src/OBPager.cc:223: error: 'mAtom_NET_NUMBER_OF_DESKTOPS' was not declared in this scope
src/OBPager.cc:223: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:223: error: 'True' was not declared in this scope
src/OBPager.cc:223: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:223: error: 'None' was not declared in this scope
src/OBPager.cc:227: error: 'mAtom_NET_SUPPORTED' was not declared in this scope
src/OBPager.cc:227: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:227: error: 'True' was not declared in this scope
src/OBPager.cc:227: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:227: error: 'None' was not declared in this scope
src/OBPager.cc:231: error: 'mAtom_NET_CLIENT_LIST_STACKING' was not declared in this scope
src/OBPager.cc:231: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:231: error: 'True' was not declared in this scope
src/OBPager.cc:231: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:231: error: 'None' was not declared in this scope
src/OBPager.cc:235: error: 'mAtom_NET_WMDESKTOP' was not declared in this scope
src/OBPager.cc:235: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:235: error: 'True' was not declared in this scope
src/OBPager.cc:235: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:235: error: 'None' was not declared in this scope
src/OBPager.cc:239: error: 'mAtom_NET_ACTIVE_WINDOW' was not declared in this scope
src/OBPager.cc:239: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:239: error: 'True' was not declared in this scope
src/OBPager.cc:239: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:239: error: 'None' was not declared in this scope
src/OBPager.cc:243: error: 'mAtom_NET_DESKTOP_GEOMETRY' was not declared in this scope
src/OBPager.cc:243: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:243: error: 'True' was not declared in this scope
src/OBPager.cc:243: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:243: error: 'None' was not declared in this scope
src/OBPager.cc:247: error: 'mAtom_NET_SUPPORTING_WM_CHECK' was not declared in this scope
src/OBPager.cc:247: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:247: error: 'True' was not declared in this scope
src/OBPager.cc:247: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:247: error: 'None' was not declared in this scope
src/OBPager.cc:251: error: 'mAtom_NET_WM_NAME' was not declared in this scope
src/OBPager.cc:251: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:251: error: 'True' was not declared in this scope
src/OBPager.cc:251: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:251: error: 'None' was not declared in this scope
src/OBPager.cc:255: error: 'mAtom_WM_NAME' was not declared in this scope
src/OBPager.cc:255: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:255: error: 'True' was not declared in this scope
src/OBPager.cc:255: error: 'XInternAtom' was not declared in this scope
src/OBPager.cc:255: error: 'None' was not declared in this scope
src/OBPager.cc: In member function 'void OBPager::createShowWindow()':
src/OBPager.cc:290: error: 'Window' was not declared in this scope
src/OBPager.cc:290: error: expected `;' before 'rootWindow'
src/OBPager.cc:304: warning: deprecated conversion from string constant to 'char*'
src/OBPager.cc:305: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:305: error: 'BlackPixel' was not declared in this scope
src/OBPager.cc:306: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:313: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:313: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:313: error: 'rootWindow' was not declared in this scope
src/OBPager.cc:313: error: 'XCreateSimpleWindow' was not declared in this scope
src/OBPager.cc:315: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:324: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:324: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:324: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:324: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:324: error: 'DefaultDepth' was not declared in this scope
src/OBPager.cc:324: error: 'XCreatePixmap' was not declared in this scope
src/OBPager.cc:326: error: no match for call to '(XPixmapKeeper) ()'
src/OBPager.cc:335: error: 'XSizeHints' was not declared in this scope
src/OBPager.cc:335: error: template argument 1 is invalid
src/OBPager.cc:335: error: invalid type in declaration before ';' token
src/OBPager.cc:337: error: request for member 'acquire' in 'mSizeHints', which is of non-class type 'int'
src/OBPager.cc:337: error: 'XAllocSizeHints' was not declared in this scope
src/OBPager.cc:339: error: 'mSizeHints' cannot be used as a function
src/OBPager.cc:344: error: 'XWMHints' was not declared in this scope
src/OBPager.cc:344: error: template argument 1 is invalid
src/OBPager.cc:344: error: invalid type in declaration before ';' token
src/OBPager.cc:346: error: request for member 'acquire' in 'mWMHints', which is of non-class type 'int'
src/OBPager.cc:346: error: 'XAllocWMHints' was not declared in this scope
src/OBPager.cc:348: error: 'mSizeHints' cannot be used as a function
src/OBPager.cc:353: error: 'XClassHint' was not declared in this scope
src/OBPager.cc:353: error: template argument 1 is invalid
src/OBPager.cc:353: error: invalid type in declaration before ';' token
src/OBPager.cc:355: error: request for member 'acquire' in 'mClassHints', which is of non-class type 'int'
src/OBPager.cc:355: error: 'XAllocClassHint' was not declared in this scope
src/OBPager.cc:357: error: 'mSizeHints' cannot be used as a function
src/OBPager.cc:366: error: base operand of '->' is not a pointer
src/OBPager.cc:367: error: base operand of '->' is not a pointer
src/OBPager.cc:368: error: base operand of '->' is not a pointer
src/OBPager.cc:369: error: base operand of '->' is not a pointer
src/OBPager.cc:370: error: base operand of '->' is not a pointer
src/OBPager.cc:370: error: 'PSize' was not declared in this scope
src/OBPager.cc:370: error: 'PMinSize' was not declared in this scope
src/OBPager.cc:370: error: 'PMaxSize' was not declared in this scope
src/OBPager.cc:372: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:372: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:372: error: 'mSizeHints' cannot be used as a function
src/OBPager.cc:372: error: 'XSetWMNormalHints' was not declared in this scope
src/OBPager.cc:377: error: base operand of '->' is not a pointer
src/OBPager.cc:377: error: 'WithdrawnState' was not declared in this scope
src/OBPager.cc:379: error: base operand of '->' is not a pointer
src/OBPager.cc:379: error: 'False' was not declared in this scope
src/OBPager.cc:380: error: base operand of '->' is not a pointer
src/OBPager.cc:380: error: no match for call to '(XPixmapKeeper) ()'
src/OBPager.cc:381: error: base operand of '->' is not a pointer
src/OBPager.cc:381: error: 'StateHint' was not declared in this scope
src/OBPager.cc:381: error: 'InputHint' was not declared in this scope
src/OBPager.cc:381: error: 'IconPixmapHint' was not declared in this scope
src/OBPager.cc:383: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:383: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:383: error: 'mWMHints' cannot be used as a function
src/OBPager.cc:383: error: 'XSetWMHints' was not declared in this scope
src/OBPager.cc:388: error: base operand of '->' is not a pointer
src/OBPager.cc:389: error: base operand of '->' is not a pointer
src/OBPager.cc:391: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:391: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:391: error: 'mClassHints' cannot be used as a function
src/OBPager.cc:391: error: 'XSetClassHint' was not declared in this scope
src/OBPager.cc:404: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:404: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:404: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:404: error: 'XCreateBitmapFromData' was not declared in this scope
src/OBPager.cc:408: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:408: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:408: error: 'ShapeBounding' was not declared in this scope
src/OBPager.cc:408: error: no match for call to '(XPixmapKeeper) ()'
src/OBPager.cc:408: error: 'ShapeSet' was not declared in this scope
src/OBPager.cc:408: error: 'XShapeCombineMask' was not declared in this scope
src/OBPager.cc:415: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:415: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:415: error: 'ExposureMask' was not declared in this scope
src/OBPager.cc:415: error: 'StructureNotifyMask' was not declared in this scope
src/OBPager.cc:415: error: 'ButtonPressMask' was not declared in this scope
src/OBPager.cc:415: error: 'XSelectInput' was not declared in this scope
src/OBPager.cc:417: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:417: error: 'PropertyChangeMask' was not declared in this scope
src/OBPager.cc:417: error: 'SubstructureNotifyMask' was not declared in this scope
src/OBPager.cc:424: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:424: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:424: error: 'XMapWindow' was not declared in this scope
src/OBPager.cc:433: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:433: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:433: error: 'XLoadQueryFont' was not declared in this scope
src/OBPager.cc:435: error: no match for call to '(XFontStructKeeper) ()'
src/OBPager.cc:444: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:444: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:446: error: no match for call to '(XFontStructKeeper) ()'
src/OBPager.cc:457: error: 'XGCValues' was not declared in this scope
src/OBPager.cc:457: error: expected `;' before 'gcValues'
src/OBPager.cc:460: error: 'gcValues' was not declared in this scope
src/OBPager.cc:460: error: no match for call to '(XFontStructKeeper) ()'
src/OBPager.cc:461: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:462: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:462: error: 'WhitePixel' was not declared in this scope
src/OBPager.cc:463: error: 'GCFont' was not declared in this scope
src/OBPager.cc:463: error: 'GCBackground' was not declared in this scope
src/OBPager.cc:463: error: 'GCForeground' was not declared in this scope
src/OBPager.cc:465: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:465: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:465: error: no match for call to '(XWindowKeeper) ()'
src/OBPager.cc:465: error: 'XCreateGC' was not declared in this scope
src/OBPager.cc:467: error: no match for call to '(XGCKeeper) ()'
src/OBPager.cc:476: error: 'XWindowAttributes' was not declared in this scope
src/OBPager.cc:476: error: expected `;' before 'rootAttributes'
src/OBPager.cc:477: error: no match for call to '(XDisplayKeeper) ()'
src/OBPager.cc:477: error: 'rootAttributes' was not declared in this scope
src/OBPager.cc:477: error: 'XGetWindowAttributes' was not declared in this scope
src/OBPager.cc: At global scope:
src/OBPager.cc:499: error: expected ',' or '...' before 'colorMap'
src/OBPager.cc:499: error: ISO C++ forbids declaration of 'Colormap' with no type
src/OBPager.cc: In member function 'long unsigned int OBPager::getColourPixel(const char*, int) const':
src/OBPager.cc:503: error: 'XColor' was not declared in this scope
src/OBPager.cc:503: error: expected `;' before 'colour'
src/OBPager.cc:505: error: no match for call to '(const XDisplayKeeper) ()'
src/OBPager.cc:505: error: 'colorMap' was not declared in this scope
src/OBPager.cc:505: error: 'colour' was not declared in this scope
src/OBPager.cc:505: error: 'XParseColor' was not declared in this scope
src/OBPager.cc:505: error: no match for call to '(const XDisplayKeeper) ()'
src/OBPager.cc:505: error: 'XAllocColor' was not declared in this scope
src/OBPager.cc:513: error: 'colour' was not declared in this scope
src/OBPager.cc: At global scope:
src/OBPager.cc:576: error: 'long int OBPager::getAtomAsLong' is not a static member of 'class OBPager'
src/OBPager.cc:576: error: 'Atom' was not declared in this scope
src/OBPager.cc:576: error: 'Atom' was not declared in this scope
src/OBPager.cc:576: error: 'Window' was not declared in this scope
src/OBPager.cc:576: error: initializer expression list treated as compound expression
src/OBPager.cc:576: error: expected ',' or ';' before 'const'
Linking obpager
g++: ./objs/src/main.o: No such file or directory
g++: ./objs/src/OBPager.o: No such file or directory
make: *** [obpager] Error 1



I was going to include it as an attachment. But apparently the file was too  big :roll:

---

### Post by stickmangumby on 2008-09-22
At a glance, that looks like you haven't got the required dependencies installed. I've never used OBPager, but apparently it requires Xlib and glibc++. Do you have them installed?

---

### Post by Mark76 on 2008-09-22
glibc++ doesn't even exist in my repository.

And I can see several xlibs, but no Xlib

---

