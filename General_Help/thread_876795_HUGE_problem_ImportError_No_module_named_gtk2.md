---
title: "HUGE problem: ImportError: No module named gtk2"
date: 2008-08-01
forum: General Help
---

### Post by genfly on 2008-08-01
ImportError: No module named gtk2

I have tried everything.... completely removing python (and therefore i had to remove all python apps and reinstall), reinstalling stuff.. tried suggestions from 20 different forum posts and nothing helps. This was a clean install of hardy heron (when it first came out). Problems started arising this week. 


Programs like cedega no longer work; F1 2008-08-01 12:25:35,302 CRITICAL Unable to load GTK2 Python bindings: No module named gtk


Other programs:
  File "/usr/bin/weather-wallpaper", line 26, in <module>
    import gtk
ImportError: No module named gtk



Terminal python stuff:

```
$ python
Python 2.5.2 (r252:60911, Jun 25 2008, 00:53:41) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
$ >>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "gtk/__init__.py", line 41, in <module>
    import gobject as _gobject
  File "/usr/local/lib/python2.5/ihooks.py", line 404, in import_module
    q, tail = self.find_head_package(parent, str(name))
  File "/usr/local/lib/python2.5/ihooks.py", line 447, in find_head_package
    raise ImportError, "No module named " + qname
ImportError: No module named gobject
```

When i typed import gtk it used to say: no module named gtk. Now it says gobject after trying 20+ different forum solution guides. 

Any help would be GREATLY appreciated. I really cant afford to reinstall ubuntu. 

Thanks in advance!!!

---

### Post by ibutho on 2008-08-01
Try importing the module as gtk2 instead of gtk. Also make sure that the python gtk modules are installed (usually called pygtk, pygtk2, python-gtk, python-gtk2 or something like that).

---

### Post by genfly on 2008-08-01
This is what i have installed

```
$ dpkg -l | grep python
ii  diveintopython                             5.4-2ubuntu2                                       free Python book for experienced programmers
ii  gimp-python                                2.4.5-1ubuntu2                                     Python support and plugins for GIMP
ii  python                                     2.5.2-0ubuntu1                                     An interactive high-level object-oriented la
ii  python-all                                 2.5.2-0ubuntu1                                     Package depending on all supported Python ru
ii  python-apport                              0.108.2                                            apport crash report handling library
ii  python-apt                                 0.7.4ubuntu7                                       Python interface to libapt-pkg
ii  python-brlapi                              3.9-6ubuntu1                                       Python bindings for BrlAPI
ii  python-cairo                               1.4.0-2ubuntu2                                     Python bindings for the Cairo vector graphic
ii  python-cairo-dbg                           1.4.0-2ubuntu2                                     Python bindings for the Cairo vector graphic
ii  python-cairo-dev                           1.4.0-2ubuntu2                                     Python cairo bindings: development files
ii  python-central                             0.6.7ubuntu0.1                                     register and build utility for Python packag
ii  python-compizconfig                        0.7.4-0ubuntu1                                     Compiz configuration system bindings
ii  python-cups                                1.9.34-0ubuntu1                                    Python bindings for CUPS
ii  python-dbg                                 2.5.2-0ubuntu1                                     Debug Build of the Python Interpreter (versi
ii  python-dbus                                0.82.4-1ubuntu1                                    simple interprocess messaging system (Python
ii  python-dev                                 2.5.2-0ubuntu1                                     Header files and a static library for Python
ii  python-elementtree                         1.2.6-11ubuntu1                                    Light-weight toolkit for XML processing
ii  python-eyed3                               0.6.14-1                                           Python module for id3-tags manipulation
ii  python-feedparser                          4.1-10                                             Universal Feed Parser for Python
ii  python-gamin                               0.1.9-2ubuntu2                                     Python binding for the gamin client library
ii  python-gconf                               2.22.0-0ubuntu1                                    Python bindings for GConf2
ii  python-gdata                               1.0.9-1ubuntu1                                     Google Data Python client library
ii  python-gdbm                                2.5.2-0ubuntu2                                     GNU dbm database support for Python
ii  python-glade2                              2.12.1-0ubuntu1                                    GTK+ bindings: Glade support
ii  python-gmenu                               2.22.2-0ubuntu1                                    an implementation of the freedesktop menu sp
ii  python-gnome2                              2.22.0-0ubuntu1                                    Python bindings for the GNOME desktop enviro
ii  python-gnome2-desktop                      2.22.0-0ubuntu1                                    Python bindings for the GNOME desktop enviro
ii  python-gnome2-extras                       2.19.1-0ubuntu7                                    Python bindings for the GNOME desktop enviro
ii  python-gnomecanvas                         2.22.0-0ubuntu1                                    Python bindings for gnomecanvas (debug exten
ii  python-gnupginterface                      0.3.2-9ubuntu1                                     Python interface to GnuPG (GPG)
ii  python-gobject                             2.14.1-2ubuntu2                                    Python bindings for the GObject library
ii  python-gobject-dbg                         2.14.1-2ubuntu2                                    Python bindings for the GObject library (deb
ii  python-gobject-dev                         2.14.1-2ubuntu2                                    Development headers for the GObject python b
ii  python-gst0.10                             0.10.11-1                                          generic media-playing framework (Python bind
ii  python-gtk2                                2.12.1-0ubuntu1                                    Python bindings for the GTK+ widget set
ii  python-gtk2-dbg                            2.12.1-0ubuntu1                                    Python bindings for the GTK+ widget set (deb
ii  python-gtk2-dev                            2.12.1-0ubuntu1                                    GTK+ bindings: devel files
ii  python-gtkhtml2                            2.19.1-0ubuntu7                                    Python bindings for the GtkHTML2 library
ii  python-gtksourceview2                      2.2.0-0ubuntu2                                     Python bindings for the GtkSourceView widget
ii  python-imaging                             1.1.6-1ubuntu5                                     Python Imaging Library
ii  python-launchpad-bugs                      0.2.30.1                                           simple Python Interface to Bugs in Launchpad
ii  python-launchpad-integration               0.1.19                                             library for launchpad integration
ii  python-ldap                                2.3.1-1ubuntu3                                     An LDAP interface module for Python
ii  python-libxml2                             2.6.31.dfsg-2ubuntu1                               Python bindings for the GNOME XML library
ii  python-minimal                             2.5.2-0ubuntu1                                     A minimal subset of the Python language (def
ii  python-mutagen                             1.11-1build1                                       audio metadata editing library
ii  python-nautilus                            0.5.0-0ubuntu3                                     Python binding for Nautilus components
ii  python-notify                              0.1.1-2                                            Python bindings for libnotify
ii  python-numeric                             24.2-8ubuntu2                                      Numerical (matrix-oriented) Mathematics for 
ii  python-numeric-dbg                         24.2-8ubuntu2                                      Numerical (matrix-oriented) Mathematics for 
ii  python-openssl                             0.6-5                                              Python wrapper around the OpenSSL library
ii  python-pexpect                             2.1-1build1                                        Python module for automating interactive app
ii  python-problem-report                      0.108.2                                            Python library to handle problem reports
ii  python-pyatspi                             1.22.1-0ubuntu1                                    Assistive Technology Service Provider Interf
ii  python-pycurl                              7.16.4-1                                           Python bindings to libcurl
ii  python-pymetar                             0.12-2.3                                           Python interface to METAR reports
ii  python-pyogg                               1.3-1.1ubuntu4                                     A Python interface to the Ogg library
ii  python-pyopenssl                           0.6-5                                              transitional dummy package
ii  python-pyorbit                             2.14.3-2ubuntu1                                    A Python language binding for the ORBit2 COR
ii  python-pysqlite2                           2.4.0-2build1                                      python interface to SQLite 3
ii  python-pyvorbis                            1.3-1.2ubuntu2                                     A Python interface to the Ogg Vorbis library
ii  python-qt3                                 3.17.4-1ubuntu4                                    Qt3 bindings for Python
ii  python-reportlab                           2.1dfsg-1ubuntu3                                   ReportLab library to create PDF documents us
ii  python-rpm                                 4.4.2.1-1ubuntu6                                   Python bindings for RPM
ii  python-sexy                                0.1.9-1ubuntu1                                     python language bindings for libsexy
ii  python-sip4                                4.7.3-1ubuntu2                                     Python/C++ bindings generator runtime librar
ii  python-software-properties                 0.63ubuntu1                                        manage the repositories that you install sof
ii  python-support                             0.7.5ubuntu1                                       automated rebuilding support for python modu
ii  python-uno                                 1:2.4.1-1ubuntu2                                   Python interface for OpenOffice.org
ii  python-urlgrabber                          3.1.0-4                                            A high-level cross-protocol url-grabber
ii  python-virtkey                             0.50ubuntu0.1                                      Library to emulate keyboard keypresses.
ii  python-vte                                 1:0.16.13-1ubuntu1                                 Python bindings for the VTE widget set
ii  python-xdg                                 0.15-1.1ubuntu3                                    A python library to access freedesktop.org s
ii  python2.4                                  2.4.5-1ubuntu4                                     An interactive high-level object-oriented la
ii  python2.4-dev                              2.4.5-1ubuntu4                                     Header files and a static library for Python
ii  python2.4-minimal                          2.4.5-1ubuntu4                                     A minimal subset of the Python language (ver
ii  python2.5                                  2.5.2-2ubuntu4                                     An interactive high-level object-oriented la
ii  python2.5-dbg                              2.5.2-2ubuntu4                                     Debug Build of the Python Interpreter (versi
ii  python2.5-dev                              2.5.2-2ubuntu4                                     Header files and a static library for Python
ii  python2.5-minimal                          2.5.2-2ubuntu4                                     A minimal subset of the Python language (ver


```

---

### Post by genfly on 2008-08-01
Thanks for the speedy reply. Pretty sure i have everything + more than i need to even.

also:

```
 >>> import gtk2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gtk2 
```

```
 >>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gtk 
```

```
 >>> import gobject
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gobject 
```


No luck :(

---

### Post by genfly on 2008-08-01
just tried installing gtk2 manually... ./configure, make, sudo make install...
installed... but nothing works still same errors everywhere.

also tried this with no luck
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo debtags update
```


Please :( someone out there must have the answer

---

### Post by genfly on 2008-08-01
<edit>

---

### Post by genfly on 2008-08-05
Great i removed Python through the terminal and it didnt just remove python packages but every package on the system. Then the system crashed. Good job Ubuntu. After some searching it looks like im not the only one this happend to. Some sort of bug.

since then ive moved to Debian. Ubuntu is WAY to unstable with packages breaking everywhere. Even Ubuntu based distro Mint is more stable with the same package release. 

Ubuntu = Debian unstable
Ubuntu < Debian Test
Ubuntu server < Debian (stable) server
Ubuntu:easy for begginers > Debian harder.

and PS yes im posting this on an Ubuntu forums. People wont agree with what im saying here. If your curious if im telling the truth do some searching for debian vs ubuntu on google and not on ubuntu forums.

---

### Post by TransplantedCanuck on 2008-08-06
I#m in pretty much the same boat, the wife installed updates (why shouldn't you?) and now almost all the administration tasks except synaptic no longer work (they won't open). 

In terminal... so not just pygtk, but gconf and gtk. 

```
maren@maren-desktop:~$ sudo su-to-root -X -c /usr/sbin/startupmanager
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 31, in <module>
    from gtk_frontend import SumGui
  File "/usr/share/startupmanager/gtk_frontend.py", line 27, in <module>
    import pygtk
ImportError: No module named pygtk
maren@maren-desktop:~$ /usr/bin/update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in <module>
    import pygtk
ImportError: No module named pygtk
maren@maren-desktop:~$ /usr/bin/gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 20, in <module>
    import gconf
ImportError: No module named gconf
maren@maren-desktop:~$ sudo gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 23, in <module>
    import gtk, gtk.glade, gobject, pynotify
ImportError: No module named gtk
```

---

### Post by e3k on 2009-10-21
> **TransplantedCanuck said:**
> I#m in pretty much the same boat, the wife installed updates (why shouldn't you?) and now almost all the administration tasks except synaptic no longer work (they won't open). 

In terminal... so not just pygtk, but gconf and gtk. 

```
maren@maren-desktop:~$ sudo su-to-root -X -c /usr/sbin/startupmanager
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 31, in <module>
    from gtk_frontend import SumGui
  File "/usr/share/startupmanager/gtk_frontend.py", line 27, in <module>
    import pygtk
ImportError: No module named pygtk
maren@maren-desktop:~$ /usr/bin/update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in <module>
    import pygtk
ImportError: No module named pygtk
maren@maren-desktop:~$ /usr/bin/gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 20, in <module>
    import gconf
ImportError: No module named gconf
maren@maren-desktop:~$ sudo gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 23, in <module>
    import gtk, gtk.glade, gobject, pynotify
ImportError: No module named gtk
```

@ [TransplantedCanuck]("http://ubuntuforums.org/member.php?u=292107")...this is an old thread but i fixed this by running:

```
sudo dpkg --configure -a
```

---

