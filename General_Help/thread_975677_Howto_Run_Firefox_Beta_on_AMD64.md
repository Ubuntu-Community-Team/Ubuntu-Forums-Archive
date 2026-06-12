---
title: "Howto: Run Firefox Beta on AMD64"
date: 2008-11-08
forum: General Help
---

### Post by Yashiro on 2008-11-08
Get the i686 version you need from here:
```
ftp://releases.mozilla.org/mozilla.org/firefox/releases/
```
Extract this into your home directory.

Get the following package to work around a bug with a missing file in ia32-libs.
```
http://mirrors.kernel.org/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.74-2_i386.deb
```
Use Archive Manager or a method of your choosing to extract
```
libdbus-glib-1.so.2.1.0
```
and rename it to 
```
libdbus-glib-1.so.2
```

Place this in the recently created ~/firefox folder (or copy it to/usr/lib32/)

Run the script named 'firefox' from within the ~/firefox folder.


For some reason the app ignores your global font smoothing settings, so it looks pretty awful. If someone knows how to correct this please contribute to this thread.

---

