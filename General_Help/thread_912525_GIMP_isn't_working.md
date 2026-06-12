---
title: "GIMP isn't working"
date: 2008-09-06
forum: General Help
---

### Post by Prominence on 2008-09-06
Title says all, I click the GIMP thing, then nothing.

---

### Post by Gerlads Mod on 2008-09-06
First, go into a terminal and type "gimp" (without quotes).
Post the output of that command.

---

### Post by Prominence on 2008-09-06
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:13678): LibGimpBase-WARNING **: gimp: wire_read(): error

---

### Post by Prominence on 2008-09-06
...any help?

---

### Post by BLTicklemonster on 2008-09-06
sudo aptitude remove gimp


then


sudo aptitude install gimp


then try again from terminal, and see what pops up.

---

### Post by Prominence on 2008-09-07
It came up, but it have me the same terminal output as above. It didn't come up with the normal gimp thing though.

---

### Post by Prominence on 2008-09-07
Nevermind I fixed it, it was an issue with a previous attempt at Gimpshop, get rid of that and its all good again.

---

### Post by BLTicklemonster on 2008-09-07
Oh, that thing again.

Never understood why people are so caught up in that issue. The desktop is your workspace, that's what different desktops are all about.

Anyway, if anyone sees this and wants to keep gimpshop for some reason, there's this:
[http://archive.debian.net/woody/all/libgimpprint-doc/download](http://archive.debian.net/woody/all/libgimpprint-doc/download)

---

