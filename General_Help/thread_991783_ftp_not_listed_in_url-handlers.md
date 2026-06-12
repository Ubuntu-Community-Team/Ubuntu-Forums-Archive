---
title: "ftp not listed in url-handlers?"
date: 2008-11-24
forum: General Help
---

### Post by moore.bryan on 2008-11-24
anyone else ever run into this problem? when i launch gconf-editor and scroll-down to desktop>gnome>url-handlers, ftp isn't listed among the output; how can that be?

---

### Post by tylerjwilk on 2012-04-17
I am seeing the same thing. FTP is launching to firefox but I dont see how to modify the handler and set it as nautilus.

---

### Post by tylerjwilk on 2012-04-17
[SOLVED]

Here are instruction to set nautilus as the default ftp handler.

$ cd /usr/share/applications
$ sudo pico firefox.desktop
--- edit the value for MimeType
------ remove x-scheme-handler/ftp;
------ save
$ sudo pico nautilus-folder-handler.desktop
--- edit the value for MimeType
------ add x-scheme-handler/ftp;
------ save
$ sudo update-desktop-database

The above actions do the following: switch to the applications config directory. remove the ftp handler from firefox. add the ftp handler to nautilus. update the desktop database of handler.

Hope that helps.

---

