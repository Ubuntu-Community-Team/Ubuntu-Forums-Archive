---
title: "Getting digiKAM to open RAF files with external applications"
date: 2008-05-12
forum: Hardware
---

### Post by jheagney on 2008-05-12
Had some difficulty with digiKAM not filling out the list of external applications that can open RAF files from my camera. A result of my camera adding uppercase file extensions to the file name rather than lowercase file extensions.

Here's the quick fix:

Open kcontrol
KDE Components -> File Associations -> image/x-raw
In the list of extensions, add an allcap version of .raf (.RAF)
Click Apply, close and restart digiKAM

Joal Heagney

---

