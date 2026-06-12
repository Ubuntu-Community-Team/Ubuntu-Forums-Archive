---
title: "problem installing mozilla's celtx"
date: 2008-09-07
forum: General Help
---

### Post by Periswell on 2008-09-07
hello

i was looking round Mozilla's application list when i found something that caught my eye named celtx so i downloaded to source code (no Linux installer).

i did the old thing in terminal of ./configure and it seemed to be going smoothly until it had this error message...

> 
checking MOZ_GTK2_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
[COLOR="Red"]configure: error: --enable-application=APP is required[/COLOR]


i don't know if i have to download something as it does not give a hint of what it is or if i have to change a file. i looked at the readme file but it does not say anything. please help.

-josh

---

### Post by Sinkingships7 on 2008-09-07
Try ```
./configure --enable-application=AP
```

---

### Post by Periswell on 2008-09-07
im afraid that did not work

-josh

---

### Post by Sinkingships7 on 2008-09-07
> **Periswell said:**
> im afraid that did not work

-josh

Did it spit out a different error message, or the same one? If it was a different message, please post the output here.

---

### Post by Periswell on 2008-09-07
no it was the same message

-josh

---

### Post by Periswell on 2008-09-07
bump

---

### Post by 500cuts on 2008-09-14
celtx the scriptwriting app?  there's a linux installer for that.

---

### Post by exile on 2009-02-24
Try making a .mozconfig or

cp mozconfig-nodebug-linux .mozconfig

---

