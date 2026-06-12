---
title: "Can't unmount USB flashdrive"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by jnoreiko on 2005-02-08
My flashdrive works as normal in Nautilus, up to the point where I try to remove it through the GUI. I get this message in a dialog, even with all apps closed:

> 
Unmounting flashdrive:

umount: /media/sda1: device is busy
umount: /media/sda1: device is busy
Error: umount failed


---

### Post by David Haas on 2005-02-13
I had the same error message when I attemped to unmount (the shell command is "umount") my floppy. The problem was solved when I disabled auto-mount in the GUI.  This is in Computer>Desktop Preferences>Removable Storage. It should be on by default and it was on my distro. I unchecked "Mount removable drives when hot-plugged, Mount removable media when inserted, and browse removable media when inserted." When I did this, I unmounted with the command (in root) "umount /media/floppy" (the directory in which I had mounted the floppy). I imagine that the umount command would have worked as well in the GUI. Try this, then.

---

