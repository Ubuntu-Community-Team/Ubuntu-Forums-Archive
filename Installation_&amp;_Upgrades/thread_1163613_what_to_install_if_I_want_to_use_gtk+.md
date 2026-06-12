---
title: "what to install if I want to use gtk+ ?"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by TKC747 on 2009-05-18
If I wanted to run the following C program, what packages would I need to install to use gtk+? Can I do this from the synaptic package manager?

#include <gtk/gtk.h>

int main( int argc, char *argv[])
{
  GtkWidget *window;

  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_widget_show(window);

  gtk_main();

  return 0;
}

---

### Post by TKC747 on 2009-05-18
the compiler gives me this error: gtk/gtk.h no such file or directory

do I need to do something with the path or such?

Thanks in advance

---

### Post by TKC747 on 2009-05-19
Sorry Problem Resolved.  I am a newbie and I didn't know the difference between a quote and a backquote](*,)

---

