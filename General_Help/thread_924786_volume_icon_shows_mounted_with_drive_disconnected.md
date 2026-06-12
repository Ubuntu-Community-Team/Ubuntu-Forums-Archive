---
title: "volume icon shows mounted with drive disconnected"
date: 2008-09-19
forum: General Help
---

### Post by dagadae on 2008-09-19
I had some hibernation issues with ubuntu (hardy) on my dell 6400.  It how shows a usb key /media/disk-1 as mounted, but the drive is disconnected.  If I reconnect the usb key, a subsequent icon is presented on the desktop and is fully functional.  The original icon can not be unmounted (right click/unmount volume)...when I try to unmount no error messages display but the volume icon remains.  fstab has no entries for this drive, but it is visible via 'Places'.

Any clues as to how to remove the volume icon???

  I have tried running gconf-editor navigating to apps/nautilus/desktop and unchecking volumes-visible.  This removes the icon, but when the box is rechecked, the spurious volume icon is displayed again.

regard dagadae

---

### Post by nowshining on 2008-09-19
more than likely you'll need to edit soem files - i found a way to remove those once but have forgotten or I have it on my 7.10 gutsy tips site :) I gotta add a couple of tipe anyway...

The /media/disk-1 should be empty and the folder should be permanent until you remove it... and as for empty it will be un-empty when u mount the needed drive..

---

