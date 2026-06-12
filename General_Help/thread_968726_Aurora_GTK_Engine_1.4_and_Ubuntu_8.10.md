---
title: "Aurora GTK Engine 1.4 and Ubuntu 8.10"
date: 2008-11-02
forum: General Help
---

### Post by Benkrishman on 2008-11-02
I'm trying to install the Aurora GTK engine 1.4 on a new 8.10 install.  I'm following the instructions here:
[http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438](http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438)


When running config I get this at the end of the output:

checking for GTK... no
configure: error: GTK+-2.10 is required to compile aurora

How do I go about getting the required packages to successfully install Aurora?

---

### Post by Partyboi2 on 2008-11-03
Try installing libgtk2.0-dev package 
```
sudo apt-get install libgtk2.0-dev
```

---

