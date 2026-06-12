---
title: "[SOLVED] Python GTK Issue"
date: 2008-10-21
forum: General Help
---

### Post by Le-Froid on 2008-10-21
EDIT: No programs that include gtk work in python...a LOT of the important stuff in my system won't work

I recently tried updating my Python installation on Ubuntu, and while updating pygtk ran into this issue while running ubuntu-tweak (I'm assuming it is a pygtk issue):

```

Traceback (most recent call last):
  File "ubuntu-tweak.py", line 22, in <module>
    import gtk
  File "/usr/local/lib/python2.5/site-packages/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/usr/local/lib/python2.5/site-packages/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/usr/local/lib/python2.5/site-packages/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /usr/local/lib/python2.5/site-packages/gtk-2.0/glib/_glib.so: undefined symbol: PySignal_SetWakeupFd

```

Does anyone know how to fix this? I tried reinstalling python from the repos, but I still get the same issue.

---

### Post by Le-Froid on 2008-10-22
***B**ring **u**p **m**y **p**ost*

---

### Post by Le-Froid on 2008-10-22
*bump* :s

---

### Post by Le-Froid on 2008-10-25
*bump* :(

---

### Post by Le-Froid on 2008-10-25
*bump*

---

### Post by Le-Froid on 2008-10-26
*bump*

---

### Post by unutbu on 2008-10-26
You might need to update your python-gtk2 package. If that does not fix the problem, please tell us which version of Ubuntu you are using (Hardy? Intrepid?)

and please also post the output of the following command:

```
dpkg --get-selections | grep python | cut -f 1 | xargs apt-cache policy
```

---

### Post by Le-Froid on 2008-10-26
> **unutbu said:**
> You might need to update your python-gtk2 package. If that does not fix the problem, please tell us which version of Ubuntu you are using (Hardy? Intrepid?)

and please also post the output of the following command:

```
dpkg --get-selections | grep python | cut -f 1 | xargs apt-cache policy
```

I have tried updating the packages already (and reinstalling them), with no success.
I'm also using 8.04, and here's the output of the command:
```

diveintopython:
  Installed: 5.4-2ubuntu2
  Candidate: 5.4-2ubuntu2
  Version table:
 *** 5.4-2ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
gimp-python:
  Installed: 2.4.5-1ubuntu2
  Candidate: 2.4.5-1ubuntu2
  Version table:
 *** 2.4.5-1ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-apport:
  Installed: 0.108.2
  Candidate: 0.108.2
  Version table:
 *** 0.108.2 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     0.108 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-apt:
  Installed: 0.7.4ubuntu7
  Candidate: 0.7.4ubuntu7
  Version table:
 *** 0.7.4ubuntu7 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-brlapi:
  Installed: 3.9-6ubuntu1
  Candidate: 3.9-6ubuntu1
  Version table:
 *** 3.9-6ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-cairo:
  Installed: 1.4.0-2ubuntu2
  Candidate: 1.4.0-2ubuntu2
  Version table:
 *** 1.4.0-2ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-cairo-dev:
  Installed: 1.4.0-2ubuntu2
  Candidate: 1.4.0-2ubuntu2
  Version table:
 *** 1.4.0-2ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-central:
  Installed: 0.6.7ubuntu0.1
  Candidate: 0.6.7ubuntu0.1
  Version table:
 *** 0.6.7ubuntu0.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     0.6.5ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-compizconfig:
  Installed: 0.7.4-0ubuntu1
  Candidate: 0.7.4-0ubuntu1
  Version table:
 *** 0.7.4-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
python-cups:
  Installed: 1.9.34-0ubuntu1
  Candidate: 1.9.34-0ubuntu1
  Version table:
 *** 1.9.34-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-dbus:
  Installed: 0.82.4-1ubuntu1
  Candidate: 0.82.4-1ubuntu1
  Version table:
 *** 0.82.4-1ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-dev:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gconf:
  Installed: 2.22.0-0ubuntu1
  Candidate: 2.22.0-0ubuntu1
  Version table:
 *** 2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gdata:
  Installed: 1.0.9-1ubuntu1
  Candidate: 1.0.9-1ubuntu1
  Version table:
 *** 1.0.9-1ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gdbm:
  Installed: 2.5.2-0ubuntu2
  Candidate: 2.5.2-0ubuntu2
  Version table:
 *** 2.5.2-0ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-glade2:
  Installed: 2.12.1-0ubuntu1
  Candidate: 2.12.1-0ubuntu1
  Version table:
 *** 2.12.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gmenu:
  Installed: 2.22.2-0ubuntu1
  Candidate: 2.22.2-0ubuntu1
  Version table:
 *** 2.22.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.22.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-gnome2:
  Installed: 2.22.0-0ubuntu1
  Candidate: 2.22.0-0ubuntu1
  Version table:
 *** 2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gnome2-desktop:
  Installed: 2.22.0-0ubuntu1
  Candidate: 2.22.0-0ubuntu1
  Version table:
 *** 2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gnome2-dev:
  Installed: 2.22.0-0ubuntu1
  Candidate: 2.22.0-0ubuntu1
  Version table:
 *** 2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gnome2-extras:
  Installed: 2.19.1-0ubuntu7.1
  Candidate: 2.19.1-0ubuntu7.1
  Version table:
 *** 2.19.1-0ubuntu7.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.19.1-0ubuntu7 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-gnomecanvas:
  Installed: 2.22.0-0ubuntu1
  Candidate: 2.22.0-0ubuntu1
  Version table:
 *** 2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gnupginterface:
  Installed: 0.3.2-9ubuntu1
  Candidate: 0.3.2-9ubuntu1
  Version table:
 *** 0.3.2-9ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gobject:
  Installed: 2.14.2-0ubuntu1
  Candidate: 2.14.2-0ubuntu1
  Version table:
 *** 2.14.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.14.1-2ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-gobject-dev:
  Installed: 2.14.2-0ubuntu1
  Candidate: 2.14.2-0ubuntu1
  Version table:
 *** 2.14.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.14.1-2ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-gst0.10:
  Installed: 0.10.11-1
  Candidate: 0.10.11-1
  Version table:
 *** 0.10.11-1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gtk2:
  Installed: 2.12.1-0ubuntu1
  Candidate: 2.12.1-0ubuntu1
  Version table:
 *** 2.12.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gtk2-dev:
  Installed: 2.12.1-0ubuntu1
  Candidate: 2.12.1-0ubuntu1
  Version table:
 *** 2.12.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-gtkhtml2:
  Installed: 2.19.1-0ubuntu7.1
  Candidate: 2.19.1-0ubuntu7.1
  Version table:
 *** 2.19.1-0ubuntu7.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.19.1-0ubuntu7 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-gtksourceview2:
  Installed: 2.2.0-0ubuntu2
  Candidate: 2.2.0-0ubuntu2
  Version table:
 *** 2.2.0-0ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-imaging:
  Installed: 1.1.6-1ubuntu5
  Candidate: 1.1.6-1ubuntu5
  Version table:
 *** 1.1.6-1ubuntu5 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-launchpad-bugs:
  Installed: 0.2.30.1
  Candidate: 0.2.30.1
  Version table:
 *** 0.2.30.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     0.2.30 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-launchpad-integration:
  Installed: 0.1.19
  Candidate: 0.1.19
  Version table:
 *** 0.1.19 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-libxml2:
  Installed: 2.6.31.dfsg-2ubuntu1.2
  Candidate: 2.6.31.dfsg-2ubuntu1.2
  Version table:
 *** 2.6.31.dfsg-2ubuntu1.2 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     2.6.31.dfsg-2ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-minimal:
  Installed: 2.5.2-0ubuntu1
  Candidate: 2.5.2-0ubuntu1
  Version table:
 *** 2.5.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-notify:
  Installed: 0.1.1-2
  Candidate: 0.1.1-2
  Version table:
 *** 0.1.1-2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-numeric:
  Installed: 24.2-8ubuntu2
  Candidate: 24.2-8ubuntu2
  Version table:
 *** 24.2-8ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-problem-report:
  Installed: 0.108.2
  Candidate: 0.108.2
  Version table:
 *** 0.108.2 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     0.108 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-pyatspi:
  Installed: 1.22.1-0ubuntu1
  Candidate: 1.22.1-0ubuntu1
  Version table:
 *** 1.22.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-pyorbit:
  Installed: 2.14.3-2ubuntu1
  Candidate: 2.14.3-2ubuntu1
  Version table:
 *** 2.14.3-2ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-pyorbit-dev:
  Installed: 2.14.3-2ubuntu1
  Candidate: 2.14.3-2ubuntu1
  Version table:
 *** 2.14.3-2ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-sexy:
  Installed: 0.1.9-1ubuntu1
  Candidate: 0.1.9-1ubuntu1
  Version table:
 *** 0.1.9-1ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-software-properties:
  Installed: 0.63ubuntu1
  Candidate: 0.63ubuntu1
  Version table:
 *** 0.63ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-support:
  Installed: 0.7.5ubuntu1
  Candidate: 0.7.5ubuntu1
  Version table:
 *** 0.7.5ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-uno:
  Installed: 1:2.4.1-1ubuntu2
  Candidate: 1:2.4.1-1ubuntu2
  Version table:
 *** 1:2.4.1-1ubuntu2 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.4.0-3ubuntu6 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-virtkey:
  Installed: 0.50ubuntu0.1
  Candidate: 0.50ubuntu0.1
  Version table:
 *** 0.50ubuntu0.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     0.50build1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python-vte:
  Installed: 1:0.16.13-1ubuntu1
  Candidate: 1:0.16.13-1ubuntu1
  Version table:
 *** 1:0.16.13-1ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python-xdg:
  Installed: 0.15-1.1ubuntu3
  Candidate: 0.15-1.1ubuntu3
  Version table:
 *** 0.15-1.1ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
python2.5:
  Installed: 2.5.2-2ubuntu4.1
  Candidate: 2.5.2-2ubuntu4.1
  Version table:
 *** 2.5.2-2ubuntu4.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     2.5.2-2ubuntu4 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python2.5-dev:
  Installed: 2.5.2-2ubuntu4.1
  Candidate: 2.5.2-2ubuntu4.1
  Version table:
 *** 2.5.2-2ubuntu4.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     2.5.2-2ubuntu4 0
        500 http://us.archive.ubuntu.com hardy/main Packages
python2.5-minimal:
  Installed: 2.5.2-2ubuntu4.1
  Candidate: 2.5.2-2ubuntu4.1
  Version table:
 *** 2.5.2-2ubuntu4.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     2.5.2-2ubuntu4 0
        500 http://us.archive.ubuntu.com hardy/main Packages

```

---

### Post by unutbu on 2008-10-26
Please post```


ls -l /usr/bin/python*
ls -l /usr/local/bin/python*
which python

```

If you see both /usr/bin/python and /usr/local/bin/python, and if 
```

which python 
```

returns

/usr/local/bin/python, then see
[http://ubuntuforums.org/showpost.php?p=5784157&postcount=21](http://ubuntuforums.org/showpost.php?p=5784157&postcount=21)

---

### Post by Le-Froid on 2008-10-26
> **unutbu said:**
> Please post```


ls -l /usr/bin/python*
ls -l /usr/local/bin/python*
which python

```

If you see both /usr/bin/python and /usr/local/bin/python, and if 
```

which python 
```

returns

/usr/local/bin/python, then see
[http://ubuntuforums.org/showpost.php?p=5784157&postcount=21](http://ubuntuforums.org/showpost.php?p=5784157&postcount=21)
it said
```

tim@linux:~/src$ ls -l /usr/bin/python*
-rwxr-xr-x 2 root root 3682516 2008-10-23 23:18 /usr/bin/python
-rwxr-xr-x 2 root root 3682516 2008-10-23 23:18 /usr/bin/python2.5
-rwxr-xr-x 1 root root    1418 2008-10-23 23:18 /usr/bin/python2.5-config
lrwxrwxrwx 1 root root      16 2008-10-23 23:18 /usr/bin/python-config -> python2.5-config
tim@linux:~/src$ ls -l /usr/local/bin/python*
-rwxr-xr-x 2 root root 3682572 2008-10-21 22:04 /usr/local/bin/python
-rwxr-xr-x 2 root root 3682572 2008-10-21 22:04 /usr/local/bin/python2.5
-rwxr-xr-x 1 root root    1424 2008-10-21 22:04 /usr/local/bin/python2.5-config
-rwxr-xr-x 1 root root 4274848 2008-10-20 20:38 /usr/local/bin/python2.6
-rwxr-xr-x 1 root root    1424 2008-10-20 20:38 /usr/local/bin/python2.6-config
lrwxrwxrwx 1 root root      16 2008-10-21 22:04 /usr/local/bin/python-config -> python2.5-config
tim@linux:~/src$ which python
/usr/local/bin/python

```

After doing that guide I still get the same error (in /usr/bin/python):
> 
Python 2.5.2 (r252:60911, Oct 23 2008, 23:17:17) 
[GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/__init__.py", line 30, in <module>
    from gobject.constants import *
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/constants.py", line 22, in <module>
    from _gobject import type_from_name
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so: undefined symbol: PyUnicodeUCS4_FromObject
>>> quit()


should I reinstall python again? - EDIT: Didn't work anyway

---

### Post by Le-Froid on 2008-10-26
*Bring up my post*

---

### Post by Le-Froid on 2008-10-26
*bump*

---

### Post by Le-Froid on 2008-10-26
Solved it - I mounted the ubuntu cd, copied all the python files, deleted my old ones, renamed some stuff, and now it works again.

---

