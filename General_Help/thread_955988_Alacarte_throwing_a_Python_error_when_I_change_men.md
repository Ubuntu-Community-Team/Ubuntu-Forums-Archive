---
title: "Alacarte throwing a Python error when I change menu entries"
date: 2008-10-22
forum: General Help
---

### Post by Sam Lars on 2008-10-22
I'm pretty sure that I removed something I shouldn't have, because alacarte is now giving me this error whenever I try to edit or add an item:
```
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 309, in on_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1153, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```
I've tried reinstalling alacarte and python2.5 and python2.5-minimal to no avail.  Maybe it's some gnome thing I removed?
Alacarte should depend on the packages it needs instead of crapping out like this...

---

### Post by entim on 2008-12-30
Just met with the same error after installing Alacarte on Gentoo.

I guess this line```
process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
```tries to execute the 'gnome-desktop-item-edit' app, but fails.

I think you should find which package contains the 'gnome-desktop-item-edit' app (probably the gnome-panel package), and reinstall that.

---

