---
title: "does ubuntu gutsy support gtk2.0"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by priyankav on 2009-04-05
i am not able to compile any gtk prog on gutsy..i get dis error

Package gtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk-2.0' found
hello.c:1:21: error: gtk/gtk.h: No such file or directory
hello.c:5: error: expected ‘)’ before ‘*’ token
hello.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘delete_event’
hello.c:30: error: expected ‘)’ before ‘*’ token
hello.c: In function ‘main’:
hello.c:40: error: ‘GtkWidget’ undeclared (first use in this function)
hello.c:40: error: (Each undeclared identifier is reported only once
hello.c:40: error: for each function it appears in.)
hello.c:40: error: ‘window’ undeclared (first use in this function)
hello.c:41: error: ‘button’ undeclared (first use in this function)
hello.c:48: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
hello.c:56: error: ‘delete_event’ undeclared (first use in this function)
hello.c:56: error: ‘NULL’ undeclared (first use in this function)
hello.c:62: error: ‘destroy’ undeclared (first use in this function)
hello.c:74: error: ‘hello’ undeclared (first use in this function)
hello.c:80: error: ‘gtk_widget_destroy’ undeclared (first use in this function)

i hav installed libgtk2.0-dev to no use
have also installed gnome-core-devel build-essential
stil does not compile
plz help!!!is it a prob with the ubuntu version??i hav 7.1(gutsy)
and in the synaptic package manager there is no gtk present

---

