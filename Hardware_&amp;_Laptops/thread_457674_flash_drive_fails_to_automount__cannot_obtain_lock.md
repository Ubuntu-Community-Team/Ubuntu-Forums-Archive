---
title: "flash drive fails to automount / cannot obtain lock on /media/.hal-mtab"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by hanasaki on 2007-05-28
Running Ubuntu Feisty 7.04

A normal user is logged into gnome and inserts a Flash Drive.  Gnome reports the below error in a dialog.[INDENT]Cannot mount volume
cannot obtain lock on /media/.hal-mtab
[/INDENT]The drive does show up in cat /proc/partitions and is mountable by root at the command like.

---

### Post by mbradlcu on 2007-05-29
this is a long shot but what happens if you add the normal users to the 'plugdev' group?

---

### Post by hanasaki on 2007-05-29
> **mbradlcu said:**
> this is a long shot but what happens if you add the normal users to the 'plugdev' group?
Same issue.  Added the user to plugdev, logged them out, restarted dbus.  Then login and try the USB flash drive.  The box cannot be bounced at this time; however, the restart of dbus + relogin (includes hald) should have ensured the new groups were picked up)

---

### Post by mfronzeo on 2007-06-05
I am experiencing the same error message with my external HD and second internal HD and additional partitions. They were accessible at one time, but it seems after I did an install updates a week or so ago the error began. The only other out of the ordinary thing I did before the error began was to burn data to a CD.
This is driving me nuts. Any help would be great.
Thanks,

---

### Post by theorem_hunter on 2007-06-10
i am also on 7.04 64bit & also cannot mount usb drives :(

---

### Post by hanasaki on 2007-07-18
Turns out that there was a conflict with path setup in my autofs automounter configs.
resolved.

---

