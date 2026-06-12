---
title: "having problems compiling compiz"
date: 2008-08-17
forum: General Help
---

### Post by stldirty on 2008-08-17
i've done this before on my computer but im on my friends computer and for some reason it wont let me make.  everytime i try it says. "make: *** No targets specified and no makefile found.  Stop."

i have build-essentials installed.  what could be the problem?

---

### Post by Locutus_of_Borg on 2008-08-17
theres no makefile
run ./configure first

---

### Post by sayakb on 2008-08-17
Instead of compiling, install it from the debian sources: [http://ubuntuforums.org/showpost.php?p=5335372&postcount=24](http://ubuntuforums.org/showpost.php?p=5335372&postcount=24)

---

### Post by stldirty on 2008-08-17
```
checking for COMPIZ... configure: error: Package requirements (x11-xcb    	 xcomposite 		 xfixes	    		 xdamage    		 xrandr    		 xinerama   		 ice	    		 sm	    	 libxml-2.0 		 libxslt    		 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

what's this about?  i've tried installing everything i can regarding x11-xcb and i'm still lost. :confused:

---

### Post by stldirty on 2008-08-17
disregard the last one.  got past that.  now im stuck on this

```
mason@mason:~/git/compiz$ make
make  all-recursive
make[1]: Entering directory `/home/mason/git/compiz'
Making all in include
make[2]: Entering directory `/home/mason/git/compiz/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mason/git/compiz/include'
Making all in src
make[2]: Entering directory `/home/mason/git/compiz/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mason/git/compiz/src'
Making all in libdecoration
make[2]: Entering directory `/home/mason/git/compiz/libdecoration'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mason/git/compiz/libdecoration'
Making all in plugins
make[2]: Entering directory `/home/mason/git/compiz/plugins'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mason/git/compiz/plugins'
Making all in images
make[2]: Entering directory `/home/mason/git/compiz/images'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mason/git/compiz/images'
Making all in gtk
make[2]: Entering directory `/home/mason/git/compiz/gtk'
Making all in window-decorator
make[3]: Entering directory `/home/mason/git/compiz/gtk/window-decorator'
/bin/bash ../../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2   -o gtk-window-decorator gtk-window-decorator.o ../../libdecoration/libdecoration.la -lXrender -lX11 -lwnck-1 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lgconf-2 -lglib-2.0 -ldbus-glib-1 -ldbus-1 -lgobject-2.0 -lglib-2.0 -lmetacity-private -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -o .libs/gtk-window-decorator gtk-window-decorator.o  ../../libdecoration/.libs/libdecoration.so -lXrender -lX11 -lwnck-1 /usr/lib/libgconf-2.so -ldbus-glib-1 -ldbus-1 -lmetacity-private /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so 
/usr/lib/libcairo.so: undefined reference to `pixman_format_supported_destination'
collect2: ld returned 1 exit status
make[3]: *** [gtk-window-decorator] Error 1
make[3]: Leaving directory `/home/mason/git/compiz/gtk/window-decorator'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mason/git/compiz/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mason/git/compiz'
make: *** [all] Error 2

```

---

