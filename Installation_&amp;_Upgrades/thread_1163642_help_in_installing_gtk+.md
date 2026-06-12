---
title: "help in installing gtk+"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by TKC747 on 2009-05-18
A tutorial I found states:

The GTK+ itself depends on the following libraries.

    * Glib
    * Pango
    * ATK
    * GDK
    * GdkPixbuf
    * Cairo
 How I can I install these libraries?  They look like nothing listed on the synaptic package manager

---

### Post by Partyboi2 on 2009-05-18
Hi, if you have Internet you can install gtk+ from the terminal
```
sudo apt-get install libgtk2.0-0
```If you need to install it to compile something else then you will need to install libgtk2.0-dev.

[B]
[/B]

---

### Post by TKC747 on 2009-05-19
> **Partyboi2 said:**
> Hi, if you have Internet you can install gtk+ from the terminal
```
sudo apt-get install libgtk2.0-0
```If you need to install it to compile something else then you will need to install libgtk2.0-dev.

[B]
[/B]

I tried that and it seems to be already installed yet I get an error message when I try to compile a program invocking gtk+:

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
the compile error basically says that there is no suchf file or directory gtk/gtk.h

---

### Post by LoloftheRings on 2009-05-19
You never mentioned COMPILING gtk+ apps!
```
sudo apt-get install libgtk2.0-dev
```

This will install development packages for gtk+.

---

### Post by TKC747 on 2009-05-19
It still doesn't work:

tommy@tommy-desktop:~$ sudo apt-get install libgtk2.0-0
[sudo] password for tommy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tommy@tommy-desktop:~$ 
tommy@tommy-desktop:~$ gcc -o testprog test.c 'pkg-config --libs --cflags gtk+-2.0'
gcc: test.c: No such file or directory
gcc: pkg-config --libs --cflags gtk+-2.0: No such file or directory
gcc: no input files
tommy@tommy-desktop:~$ cd Desktop
tommy@tommy-desktop:~/Desktop$ gcc -o testprog test.c 'pkg-config --libs --cflags gtk+-2.0'
gcc: pkg-config --libs --cflags gtk+-2.0: No such file or directory
test.c:1:21: error: gtk/gtk.h: No such file or directory
test.c: In function ‘main’:
test.c:5: error: ‘GtkWidget’ undeclared (first use in this function)
test.c:5: error: (Each undeclared identifier is reported only once
test.c:5: error: for each function it appears in.)
test.c:5: error: ‘window’ undeclared (first use in this function)
test.c:9: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
tommy@tommy-desktop:~/Desktop$

---

### Post by Partyboi2 on 2009-05-19
You need the dev package of libgtk2.0-0, so as already posted open a terminal and install with
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by TKC747 on 2009-05-19
Thanks for all the input.

I actually didn't use a backquote: ` as I should have
Problem resolved.  I should have known there was a difference...DUH!](*,)

---

