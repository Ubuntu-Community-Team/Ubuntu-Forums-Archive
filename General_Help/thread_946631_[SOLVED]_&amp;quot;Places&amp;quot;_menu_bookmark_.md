---
title: "[SOLVED] &amp;quot;Places&amp;quot; menu bookmark will not delete"
date: 2008-10-13
forum: General Help
---

### Post by benpage26 on 2008-10-13
Hello,

On ubuntu's main menu in the "places > bookmarks" folder i have a link to a filesystem that i cannot remove.  Can anyone help me?

I tried opening Gedit's file>save dialog and removing from there, but it doesn't appear there.

All help appreciated :D

---

### Post by shawnrgr on 2008-10-13
unmount the drive, it should remove the shortcut

---

### Post by kerry_s on 2008-10-13
places is in nautilus, so open your home, right click the entry> remove.

---

### Post by Yellow Pasque on 2008-10-13
The bookmarks are stored in ~/.gtk-bookmarks
```
gedit ~/.gtk-bookmarks
```

---

### Post by benpage26 on 2008-10-15
Thanks for you help guys, I tried both ways and they worked, but i didn't know how to unmount the drive as it wasn't really mounted (not in Computer or 'Media' in nautilus)

Marking solved

---

### Post by Yellow Pasque on 2008-10-15
To see what's mounted:
```
cat /etc/mtab
```
To unmount something:
```
sudo umount <name of directory where it's mounted>
```

---

