---
title: "Kazehakase Always Crashes When I Try To Open An Url"
date: 2008-09-28
forum: General Help
---

### Post by Mark76 on 2008-09-28
Which is really of very little use in a browser :rolleyes:

 > kazehakase

(kazehakase:9192): Kazehakase-CRITICAL **: kz_tab_label_new: assertion `KZ_IS_EMBED(kzembed)' failed

(kazehakase:9192): Gtk-CRITICAL **: gtk_widget_show_all: assertion `GTK_IS_WIDGET (widget)' failed

(kazehakase:9192): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(kazehakase:9192): Gtk-CRITICAL **: gtk_notebook_insert_page: assertion `GTK_IS_WIDGET (child)' failed

(kazehakase:9192): Kazehakase-CRITICAL **: kz_notebook_get_sibling_tab_label: assertion `KZ_IS_TAB_LABEL(label)' failed
Segmentation fault


I have 0.5.5

---

### Post by kagashe on 2008-09-28
I am running 0.5.4 on Debian Lenny. It was running ok on IceWM and LXDE but giving segmentation fault on Gnome. I searched Debian bugs for Kazehakase and got a workaround. Delete ~/.kazehakase/clip.xml

Now it is working on Gnome as well and I am posting this on Kazehakase.

kagashe

---

