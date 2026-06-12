---
title: "apt-get not resolving dependencies?"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by omfgbunnies on 2009-09-16
I'm having terrible trouble here. After two fresh installs (9.04 server lts) I'm a bit further on with installing [Deluge]("http://www.deluge-torrent.org"), but now am up against apt-get's refusal to resolve dependencies.

I added
```
deb http://ppa.launchpad.net/deluge-team/ubuntu jaunty main universe
```

to the /etc/apt/sources.list file, and did the GPG fix mentioned [here]("http://ubuntuforums.org/showthread.php?t=1056099") (as apt-get update wouldn't work until this was done) - however when I come to install Deluge, I'm thrown up this error:

```
# apt-get install deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  deluge: Depends: python (>= 2.5) but it is not going to be installed
          Depends: python-support (>= 0.7.1) but it is not going to be installed
          Depends: deluge-common (= 1.1.9+dfsg-2~jaunty~ppa1) but it is not going to be installed
          Depends: python-glade2 but it is not going to be installed
          Depends: python-notify but it is not going to be installed
          Depends: python-dbus but it is not going to be installed
E: Broken packages
```


It's slightly different to what I received the first time, because one of the many pages I visited on my endless trawl through Google mentioned they'd had success after uninstalling python and reinstalling it. The problem I have is that when I try to install python alone, it gives me similar errors:


```
# apt-get install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  python: Depends: python-minimal (= 2.5.2-3ubuntu1) but 2.6.2-0ubuntu1 is to be installed
E: Broken packages
```


I have trawled the Deluge FAQs and forums but can't seem to find an answer. Where can I go from here? I'm at a total loss, as I'm not an expert on Ubuntu, and have no intention to put an X server on the box.

Help much appreciated :)

---

### Post by zvacet on 2009-09-16
```
sudo apt-get -f install
```

or you can try

```
sudo aptitude install deluge
```

---

### Post by omfgbunnies on 2009-09-16
Unfortunately the first command (which I have tried previously) does this:

```
# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And the second command did exactly what I wanted, thankyou! :)

How on earth does one way fail so miserably?

---

### Post by omfgbunnies on 2009-09-16
Of course, if it ever were that simple...

```
# deluge
[ERROR   ] 17:21:22 config:293 Error backing up old config..
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
1.1.9
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:60: Warning: invalid (NULL) pointer instance
  "glade/queuedtorrents.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:60: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  "glade/queuedtorrents.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:60: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  "glade/queuedtorrents.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:60: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  "glade/queuedtorrents.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:60: Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
  "glade/queuedtorrents.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:76: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  gtk.TreeViewColumn(_("Torrent"), gtk.CellRendererText(), text=0))
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:76: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  gtk.TreeViewColumn(_("Torrent"), gtk.CellRendererText(), text=0))
[ERROR   ] 17:21:23 config:293 Error backing up old config..
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: Warning: invalid (NULL) pointer instance
  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: Invalid icon size 1

  "glade/main_window.glade"))
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
  "glade/main_window.glade"))
Segmentation fault
```


I guess Python is knackered?

---

### Post by wojox on 2009-09-16
Your trying to download a GUI to the server. That's what's giving you the GTK+ errors.

You would probably be better of downloading  a command line version:

[http://www.cyberciti.biz/tips/linux-command-line-bittorrent-client.html](http://www.cyberciti.biz/tips/linux-command-line-bittorrent-client.html)

---

### Post by omfgbunnies on 2009-09-16
Deluge has a CLI.

I missed a part of it and it seems 

```
# deluge -u console
```

launches the cli version.


Seems sorted. Thanks.

---

