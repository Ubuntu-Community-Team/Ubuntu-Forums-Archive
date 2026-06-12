---
title: "Radeon driver issue with 13.10"
date: 2014-01-12
forum: Hardware
---

### Post by rem8114 on 2014-01-12
Looked through lots of posts regarding radeon driver but haven't been able to get the driver to work correctly.  I upgraded from 12.04 (using fglrx and working fine) to 12.10/13.04/13.10.  Now using the open source radeon driver (fully removed fglrx).  HD3000 (RS780).  Connected to 1600x900 monitor.

Login screen works fine (full resolution), but when I login the screen "shreds".  tty works(f1 to f6).  If I use recovery mode and resume it sets the resolution to 1024x768 and it logs in fine, but there are no higher monitor settings.

---

### Post by QIII on 2014-01-12
Hello!

When doing a series of upgrades like that, nearly anything can go wrong.  You may end up being better off doing a clean install.

But let's set that aside for a bit.

Could you get a picture of the screen with a cell phone or something and post it?  Please remember to use the "paper clip" button to use the attachment functionality.

---

### Post by rem8114 on 2014-01-12
Started to take pics and found it was only the ubuntu studio (XFCE) interface that had the issue.  I was able to get the ubuntu default to work (after re-installing the desktop packages).  Never got the xfce desktop to work so removed the xfce packages.

---

