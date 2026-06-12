---
title: "OpenBOX + Nautilus = NO Connect to server"
date: 2008-09-11
forum: General Help
---

### Post by azanutta on 2008-09-11
hi.. i need to connect to a device via WebDav.. i know that Thunar doesn't support it so i execute the command from an openbox-only session to invoke nautilus --no desktop ....
remembering how to do when i open the gnome session, if i click FILE > Connect to server, the window that opens doesnt contain any of the methods that are available if i run nautilus in the gnome session (SSH, WEBDAV, FTP.. etc..)
so i'm wondering if there's a command to include in the autostart.sh of openbox to strt a particular daemon that controls these connections...
i've also noticed that in nautilus i'm not able to browse the "places" folder NETWORK... could it be the same problem?!?
thanks in advance!

---

### Post by azanutta on 2008-09-11
ok, i've found that could be related to the gvfs package... more specfic to the gvfsd-dav package...
but now...how can i run this process... i've gvfsd-dav the terminal but it doesn't work...
anyone?!?

---

### Post by azanutta on 2008-09-12
bump

---

