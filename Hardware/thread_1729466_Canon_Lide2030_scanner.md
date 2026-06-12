---
title: "Canon Lide20/30 scanner"
date: 2011-04-15
forum: Hardware
---

### Post by ELMIT on 2011-04-15
This Canon Lide 20/30 scanner served me for many years.

Now I get the problem that I cannot switch to any other solution than 300. If I try the program Xsane will crash.
If I try to use xsane from the command line I see:

(xsane:12293): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Segmentation fault



Any idea how to solve that?


bye

Ronald

---

### Post by ELMIT on 2011-04-15
I tried:

scanimage --resolution 600 -x 100 -y 100 --mode color

and it did not crash!
I think that this means that Xsane has something wrong!



bye

Ronald

---

### Post by ELMIT on 2011-04-15
> It has been solved by first deleting the directory ~/.sane and then again starting 'xsane'. It seems that
the previous configuration was not compatible with the latest version of 'xsane'.


Solved!

---

