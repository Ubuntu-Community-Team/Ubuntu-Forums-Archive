---
title: "Recent Docs"
date: 2008-12-01
forum: General Help
---

### Post by tubular on 2008-12-01
under "places" menu on the desktop "recent docs" is greyed out and is never highlighteable ??

---

### Post by jakupl on 2008-12-01
I'm not really sure, but can you post the output of
```
cat .recently-used.xbel
```

remember to wrap in in [CO******DE] [/C******ODE] tags

EDIT: this might show us every file you have visited, so don't do it if you don't want to :)

---

### Post by tubular on 2008-12-01
Could not find in Home...
but In terminal ?
states "Is a directory"

---

### Post by jakupl on 2008-12-01
okay, Can you go to terminal and post the output of

```
ls -lA
```

---

### Post by tubular on 2008-12-03
```
total 78
drwx------  3  80 2008-11-20 08:16 .adobe
-rw-------  1  3137 2008-12-03 13:46 .bash_history
-rw-r--r--  1  220 2008-11-19 16:58 .bash_logout
-rw-r--r--  1 3115 2008-11-19 16:58 .bashrc
drwxr-xr-x  4  96 2008-11-20 15:43 .cache
drwxr-xr-x  4 152 2008-11-20 15:37 .clamtk
drwxr-xr-x 11  424 2008-12-03 13:43 .config
drwx------  3  80 2008-11-19 17:05 .dbus
drwxr-xr-x  2   48 2008-12-03 09:24 Desktop
-rw-------  1     2 2008-12-03 13:43 .dmrc
drwxr-xr-x  2  48 2008-11-19 17:05 Documents
-rw-------  1  16 2008-11-19 17:05 .esd_auth
drwxr-xr-x  3   80 2008-11-21 23:13 .evolution
lrwxrwxrwx  1   26 2008-11-19 16:58 Examples -> /usr/share/example-content
drwxr-xr-x  2 1968 2008-11-28 09:44 .fontconfig
drwx------  5 120 2008-12-03 13:43 .gconf
drwx------  2   80 2008-12-03 13:47 .gconfd
drwx------  8  264 2008-11-19 21:00 .gdesklets
drwx------  4    96 2008-11-20 23:05 .gegl-0.0
drwxr-xr-x 22  896 2008-12-01 19:54 .gimp-2.6
-rw-r-----  1 0 2008-12-03 09:25 .gksu.lock
drwx------ 14   632 2008-12-03 09:29 .gnome2
drwx------  2    48 2008-11-19 17:06 .gnome2_private
drwx------  2    72 2008-11-19 17:06 .gnupg
drwxr-xr-x  2    88 2008-11-20 20:28 .gstreamer-0.10
-rw-r--r--  1  116 2008-12-03 13:43 .gtk-bookmarks
dr-x------  2   0 2008-12-03 13:43 .gvfs
-rw-------  1  4602 2008-12-03 13:43 .ICEauthority
drwxr-xr-x  2    48 2008-11-19 17:47 .icons
drwx------  3  192 2008-11-25 09:34 .kde
drwx------  3  72 2008-11-19 17:06 .local
drwx------  3   80 2008-11-20 08:16 .macromedia
drwxr-xr-x  3   112 2008-11-25 12:37 .mcop
-rw-------  1  31 2008-11-25 12:37 .mcoprc
drwx------  4 104 2008-11-19 17:42 .mozilla
drwxr-xr-x  2  128 2008-11-24 19:48 Music
drwxr-xr-x  3  3440 2008-12-03 09:29 .nautilus
drwx------  3  72 2008-11-29 15:50 .openoffice.org2
drwxr-xr-x  2   440 2008-11-19 20:43 Pictures
-rw-r--r--  1   675 2008-11-19 16:58 .profile
drwxr-xr-x  2    48 2008-11-19 17:05 Public
drwxr-xr-x  2  88 2008-11-19 17:06 .pulse
-rw-------  1   256 2008-11-19 17:05 .pulse-cookie
drwxr-xr-x  2   120 2008-11-25 12:37 .qt
drwxr-xr-x  2    48 2008-11-21 21:50 .recently-used
drw-------  2    48 2008-11-21 21:50 .recently-used.xbel
drwxr-xr-x  2    80 2008-11-20 14:52 .screenlets
-rw-r--r--  1     0 2008-11-19 17:07 .sudo_as_admin_successful
drwxr-xr-x  2  8 2008-11-19 17:05 Templates
drwxr-xr-x  2  48 2008-11-19 17:47 .themes
drwx------  4  96 2008-11-21 19:56 .thumbnails
drwxr-xr-x  4 264 2008-11-19 21:30 .tomboy
-rw-r--r--  1 5662 2008-11-19 21:30 .tomboy.log
drwxr-xr-x  2 80 2008-11-19 17:07 .update-manager-core
drwx------  2  48 2008-11-19 17:06 .update-notifier
-rw-r--r--  1 root    root      31 2008-11-20 23:18 .usb-creator.log
drwxr-xr-x  2 48 2008-11-19 17:05 Videos
drwxr-xr-x  2 48 2008-11-19 21:30 .wapi
drwxr-xr-x  4 232 2008-12-03 07:54 .wine
-rw-------  1 126 2008-12-03 13:43 .Xauthority
-rw-r--r--  1 129 2008-11-21 17:32 .xscreensaver-getimage.cache
-rw-r--r--  1 5635 2008-12-03 13:47 .xsession-errors



```

---

### Post by tubular on 2008-12-06
recent docs is still greyed out under the "places" menu - it used to be active when I first installed Ubuntu...after a few days it became grey and un-clickable.

---

### Post by tubular on 2008-12-15
no suggestions ?

---

