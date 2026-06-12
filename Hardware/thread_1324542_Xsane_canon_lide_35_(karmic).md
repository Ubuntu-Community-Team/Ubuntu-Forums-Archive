---
title: "Xsane canon lide 35 (karmic)"
date: 2009-11-12
forum: Hardware
---

### Post by Hakimjo on 2009-11-12
Hello - Xsane is supposed to support the Canon lide 35 scanner.  It does recognise it.  But when trying to preview the scan, it returns the infamous "invalid argument" error.  Has anybody solved this problem without buying a hp scanner ?

---

### Post by desertdog on 2009-11-16
Try opening a terminal and typing $sane-find-scanner or $lsusb.
Your scanner should be listed.

Next type $sudo scanimage -L and see if your scanner is still listed.

Next type $scanimage -L  (without sudo) and see if it is still listed.

If it works as sudo, but not as regular user, then it is a permission issue with either udev rules or hal.

---

### Post by Hakimjo on 2009-11-16
> **desertdog said:**
> Try opening a terminal and typing $sane-find-scanner or $lsusb.
Your scanner should be listed.

Next type $sudo scanimage -L and see if your scanner is still listed.

Next type $scanimage -L  (without sudo) and see if it is still listed.

If it works as sudo, but not as regular user, then it is a permission issue with either udev rules or hal.


With or without sudo, scanimage -L returns this:

WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `genesys:libusb:002:006' is a Canon LiDE 35/40/50 flatbed scanner

Maybe I just have to get rid of this message in some config file ?

Thanks for leading me through the desert

Jo

---

### Post by desertdog on 2009-11-16
You could post your question on the mailing list at [http://www.sane-project.org/mailing-lists.html](http://www.sane-project.org/mailing-lists.html).

---

