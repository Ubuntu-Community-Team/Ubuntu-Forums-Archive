---
title: "Problem launching admin tasks"
date: 2008-10-19
forum: General Help
---

### Post by M4rotku on 2008-10-19
Hello all,

I've had this problem twice now with two different programs.  When I try to start either of the following programs
[LIST]
[*]Printing
[*]StartUpManager
[/LIST]

from the menu, I receive no response.  When I try to launch them from the terminal, I receive the following output:

> $ sudo startupmanager 
[sudo] password for user: 
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 31, in <module>
    from gtk_frontend import SumGui
  File "/usr/share/startupmanager/gtk_frontend.py", line 27, in <module>
    import pygtk
ImportError: No module named pygtk


and

> $ /usr/bin/system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 29, in <module>
    import gtk.glade
ImportError: No module named gtk.glade


How can I fix this.  I really need to be able to use these two programs.

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-10-20
bump

---

### Post by M4rotku on 2008-10-21
bump

---

### Post by MaxIBoy on 2008-10-21
Try downloading pygtk ([www.pygtk.org](www.pygtk.org),) because that's what seems to be missing in both cases.

Also, one of them seems to be missing the package "python-glade2" so you should install that from the repos.

---

### Post by M4rotku on 2008-10-22
I should've explained a bit more.  I had those both installed so that I could try to great a GUI with glade.  It was when I installed those programs that this problem began to occur.

Since I thought that it was caused by those programs, I removed them and now the problem is still there.

---

