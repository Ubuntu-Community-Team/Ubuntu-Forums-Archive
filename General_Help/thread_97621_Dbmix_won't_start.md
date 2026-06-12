---
title: "Dbmix won't start"
date: 2005-12-01
forum: General Help
---

### Post by `GooZ´ on 2005-12-01
Hi,

I installed dbmix, but it won't load, so I gave in the command 'dbmixer' in the terminal, to see what was wrong, this is the error I got:

```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",DBMixer ERROR: could not create shared memory for system data.: No such file or directory
DBMixer: could not detach memory segment.: Invalid argument

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkObject'

Gtk-CRITICAL **: file gtksignal.c: line 724 (gtk_signal_connect): assertion `object != NULL' failed.
```

---

### Post by dmacdonald111 on 2006-04-28
I get the same error, but without the libsmooth.so lines. Strange one this, I cannot seem to find any support for it.

---

### Post by kurtkraut on 2006-06-24
Hi,


Run the program dbfsd before running dbmixer.

---

