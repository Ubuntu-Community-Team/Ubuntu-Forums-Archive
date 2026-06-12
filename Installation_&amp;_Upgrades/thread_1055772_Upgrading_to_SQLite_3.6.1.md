---
title: "Upgrading to SQLite 3.6.1"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by zspace on 2009-01-31
I'm trying to get something to compile from source and keep running into an error involving my sqlite version. The source requires sqlite 3.6.1 or higher, but only 3.5.9 (the version that comes with Ubuntu 8.1) is listed in the apt-get databases.
I tried downloading the source and from the looks of it, it is installing the new version correctly (3.6.1), but I am still getting the error upon trying to compile the first source code.
If anyone know what is wrong that would be helpful. The only thing I have to go on is a message output during the "sudo make install" for the sqlite code:

From the end of "make" during sqlite compile:
```
shell.c:1182: warning: format not a string literal and no format arguments
/bin/bash ./libtool --tag=CC --mode=link gcc -DSQLITE_THREADSAFE=1  -g -O2   -o sqlite3  shell.o ./libsqlite3.la -lcurses  -ldl -lpthread 
gcc -DSQLITE_THREADSAFE=1 -g -O2 -o .libs/sqlite3 shell.o  ./.libs/libsqlite3.so -lcurses -ldl -lpthread 
creating sqlite3
```

This makes me thing that it worked.
Then during "sudo make install" I get:
```
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.


```

I really have no idea what this means, but I do believe it to be the source of my problem. If anyone could interpret, and tell me what I need to add?

---

