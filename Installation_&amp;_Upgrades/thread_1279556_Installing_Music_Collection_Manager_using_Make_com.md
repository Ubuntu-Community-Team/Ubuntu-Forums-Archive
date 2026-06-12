---
title: "Installing Music Collection Manager using Make command"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by runnerjosh on 2009-10-01
I'm trying to install a program I found on Sourceforge.net called Music Collection Manager.  The program can be found at [http://sourceforge.net/projects/duplicates/](http://sourceforge.net/projects/duplicates/) .
I'm betting there is a pretty easy solution, but it's not coming to me at all.  Thank you for any help.

The install file says the following

To install de Music Collection Manager, follow these steps:
1: Edit defines.h. The paths should be like: "your homedir"/.mcm/*. Do not use a ~, but type your full homedir path.
2: run 'make'
3: run 'make install'. This will copy the executable to ~/bin and some stuff to ~/.mcm

so I changed the file to 
#define DBNAME        "/home/josh/programs/.mcm/mcm_db"
#define    CONFIG_FILE    "/home/josh/programs/.mcm/mcm_config"
#define TABLES_PATH    "/home/josh/programs/.mcm/tables"
#define HOMEDIR        "/home/josh/programs/"

The extracted files are in the folder mcm and mcm is in the a folder I called programs which is in my home folder and I'm josh.
and when this didn't work I got rid of # signs.  Still didn't work when I tried running sudo make and sudo make install.  Also I'm in the mcm directory when I run them.

Oh and I do the the build essentials installed.

Thank you for any help you can give.  :)  Also below is what I put in the terminal

josh@jibm:~$ cd /home/josh/programs/mcm
josh@jibm:~/programs/mcm$ sudo make
[sudo] password for josh: 
gcc -O2   -c -o fft.o fft.c
gcc -O2   -c -o mfcc.o mfcc.c
gcc -O2   -c -o energy_diff.o energy_diff.c
gcc -O2   -c -o extractor.o extractor.c
gcc -O2   -c -o db.o db.c
db.c:30:23: error: gdbm/ndbm.h: No such file or directory
db.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
db.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dcounter’
db.c: In function ‘init_db’:
db.c:43: error: ‘datum’ undeclared (first use in this function)
db.c:43: error: (Each undeclared identifier is reported only once
db.c:43: error: for each function it appears in.)
db.c:43: error: expected ‘;’ before ‘t’
db.c:45: error: ‘db’ undeclared (first use in this function)
db.c:48: error: ‘dcurId’ undeclared (first use in this function)
db.c:52: error: ‘dcounter’ undeclared (first use in this function)
db.c:54: error: ‘t’ undeclared (first use in this function)
db.c:62: error: ‘DBM_INSERT’ undeclared (first use in this function)
db.c:69: error: request for member ‘dptr’ in something not a structure or union
db.c: In function ‘set’:
db.c:76: error: ‘datum’ undeclared (first use in this function)
db.c:76: error: expected ‘;’ before ‘d1’
db.c:87: error: ‘d1’ undeclared (first use in this function)
db.c:90: error: ‘d2’ undeclared (first use in this function)
db.c:92: error: ‘db’ undeclared (first use in this function)
db.c:92: error: ‘DBM_INSERT’ undeclared (first use in this function)
db.c: In function ‘exists’:
db.c:163: error: ‘datum’ undeclared (first use in this function)
db.c:163: error: expected ‘;’ before ‘d’
db.c:165: error: ‘d’ undeclared (first use in this function)
db.c:168: error: ‘d2’ undeclared (first use in this function)
db.c:168: error: ‘db’ undeclared (first use in this function)
db.c: In function ‘get_mfcc’:
db.c:176: error: ‘datum’ undeclared (first use in this function)
db.c:176: error: expected ‘;’ before ‘key’
db.c:182: error: ‘key’ undeclared (first use in this function)
db.c:184: error: ‘value’ undeclared (first use in this function)
db.c:184: error: ‘db’ undeclared (first use in this function)
db.c: In function ‘get_energy’:
db.c:199: error: ‘datum’ undeclared (first use in this function)
db.c:199: error: expected ‘;’ before ‘key’
db.c:205: error: ‘key’ undeclared (first use in this function)
db.c:207: error: ‘value’ undeclared (first use in this function)
db.c:207: error: ‘db’ undeclared (first use in this function)
db.c: In function ‘get_date’:
db.c:221: error: ‘datum’ undeclared (first use in this function)
db.c:221: error: expected ‘;’ before ‘key’
db.c:227: error: ‘key’ undeclared (first use in this function)
db.c:229: error: ‘value’ undeclared (first use in this function)
db.c:229: error: ‘db’ undeclared (first use in this function)
db.c: In function ‘get’:
db.c:243: error: ‘datum’ undeclared (first use in this function)
db.c:243: error: expected ‘;’ before ‘key’
db.c:259: error: ‘key’ undeclared (first use in this function)
db.c:261: error: ‘value’ undeclared (first use in this function)
db.c:261: error: ‘db’ undeclared (first use in this function)
db.c: In function ‘get_size’:
db.c:313: error: ‘db’ undeclared (first use in this function)
db.c:313: error: ‘dcounter’ undeclared (first use in this function)
db.c:313: error: request for member ‘dptr’ in something not a structure or union
db.c: In function ‘list’:
db.c:317: error: ‘datum’ undeclared (first use in this function)
db.c:317: error: expected ‘;’ before ‘key’
db.c:330: error: ‘key’ undeclared (first use in this function)
db.c:330: error: ‘db’ undeclared (first use in this function)
db.c:335: error: ‘value’ undeclared (first use in this function)
db.c:340: error: ‘key2’ undeclared (first use in this function)
db.c: In function ‘delete’:
db.c:396: error: ‘datum’ undeclared (first use in this function)
db.c:396: error: expected ‘;’ before ‘key’
db.c:402: error: ‘key’ undeclared (first use in this function)
db.c:404: error: ‘value’ undeclared (first use in this function)
db.c:404: error: ‘db’ undeclared (first use in this function)
db.c: In function ‘store_counter’:
db.c:437: error: ‘datum’ undeclared (first use in this function)
db.c:437: error: expected ‘;’ before ‘dat’
db.c:443: error: ‘dat’ undeclared (first use in this function)
db.c:445: error: ‘db’ undeclared (first use in this function)
db.c:445: error: ‘dcounter’ undeclared (first use in this function)
db.c:445: error: ‘DBM_REPLACE’ undeclared (first use in this function)
db.c: In function ‘store_id’:
db.c:452: error: ‘datum’ undeclared (first use in this function)
db.c:452: error: expected ‘;’ before ‘dat’
db.c:458: error: ‘dat’ undeclared (first use in this function)
db.c:460: error: ‘db’ undeclared (first use in this function)
db.c:460: error: ‘dcurId’ undeclared (first use in this function)
db.c:460: error: ‘DBM_REPLACE’ undeclared (first use in this function)
db.c: In function ‘close_db’:
db.c:473: error: ‘db’ undeclared (first use in this function)
make: *** [db.o] Error 1

---

### Post by lemming465 on 2009-10-09
Personally, I think I'd give up on this; it appears to be fairly old, unmaintained code.

About "defines.h", your original edits looked OK; when you tried
> I got rid of # signs
that would make things worse, not better.  This is C code and a C include file; #define is part of the C preprocessor macro syntax and the # is required.  Put them back!
> db.c:30:23: error: gdbm/ndbm.h: No such file or directory
This is a two-fold problem:
1) you are probably missing some dependencies
2) db.c has
```

#ifdef __linux__
#include <gdbm/ndbm.h>
#else
#include <ndbm.h>
#endif

```
which won't work even after installing the dependencies, because the include file (on Ubuntu 9.04 "jaunty jackolope") is actually called /usr/include/gdbm-ndbm.h.

Also once you fix those two, you will still have a link-time problem in the Makefile;
the LDFLAGS need to specify *-lgdbm_compat*, not -lgdbm.

A patch for the problems I described above is:
```
--- mcm/db.c	2003-05-13 08:01:33.000000000 -0500
+++ mcm-bad-fix/db.c	2009-10-09 10:15:00.398148848 -0500
@@ -27,7 +27,7 @@
 #include <fcntl.h>
 #include <string.h>
 #ifdef __linux__
-#include <gdbm/ndbm.h>
+#include <gdbm-ndbm.h>
 #else
 #include <ndbm.h>
 #endif

diff -ru mcm/Makefile mcm-bad-fix/Makefile
--- mcm/Makefile	2003-05-13 07:52:34.000000000 -0500
+++ mcm-bad-fix/Makefile	2009-10-09 10:25:58.329145844 -0500
@@ -4,7 +4,7 @@
 #GTKFLAGS = -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include -I/usr/lib/gnome-libs/include
 GTKFLAGS = -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include
 #LDFLAGS = -rdynamic -lgnomeui -lart_lgpl -lgdk_imlib -lgtk -lgdk -lgmodule -lgnome -lgnomesupport -lesd -laudiofile -lglib -ldl -lpthread -lm -lgdbm -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include
-LDFLAGS = -lgdk -lgtk -lpthread -lm -lgdbm
+LDFLAGS = -lgdk -lgtk -lpthread -lm -lgdbm_compat
 
 OBJS = fft.o mfcc.o energy_diff.o extractor.o db.o comparator2.o compare.o filehandler/common.o filehandler/decode.o filehandler/huffman.o filehandler/ieeefloat.o filehandler/portableio.o filehandler/filehandler.o replace.o configfile.o gui/interface.o gui/callbacks.o gui/main.o gui/thread.o mp3info/header.o mp3info/id3extract.o
```
You should be able apply the patch changes with something like
```

cd mdm
cat > jiml.patch
# paste the patch lines from above here
Ctrl-D
patch -p1 < jiml.patch

```
You can install the most glaringly missing libraries by
```

sudo aptitude install libgdbm-dev libgtk1.2-dev

```

At this point the *make* step should run to completion, albeit with some compilation warning messages.  But the resulting "mcm" binary probably still won't run succesfully. 

When I tried it, mcm died because it's expecting to see a GTK 1.2 version of *libcanberra-gtk-module.so*, and Ubuntu is only providing the GTK 2.0 version of that.  This is the point where I gave up; I'm not sure what other problems there might be, and I lack both the time and the experience with GTK to try porting the code to a later version.

---

### Post by runnerjosh on 2009-10-19
Thanks for the help!

---

