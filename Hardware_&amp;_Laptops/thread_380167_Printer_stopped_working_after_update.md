---
title: "Printer stopped working after update"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by freesun on 2007-03-09
Well, my Samsung SCX-4100 printer stopped working after CUPS update... I know it is because it is GDI so it needs to replace some of CUPS files to work. But driver won't install now. Is there a way to roll back to previous version of CUPS?

---

### Post by justwannasearch on 2007-03-09
My printer (HP-PSC 2175) also stopped working after a system update this morning. But I dont think that a new version of cups has been installed (nor do i have modified my installation).

Someone has a clue what could be wrong?

OK, got my problem solved using this instructions: [http://ubuntuforums.org/showthread.php?p=2270082#post2270082](http://ubuntuforums.org/showthread.php?p=2270082#post2270082)
freesun: my problem was not cups related at all (it was some wrong udev rules), but u could look at the thread anyways. Maybe it'll help you too. Good luck.

---

### Post by freesun on 2007-03-10
well I examined that post but it provides no help to me, as my file contains already SYSFS. Any help? My driver installation states that ERROR: HARDWARE_PLATFORM undefined, execution aborted


thanks...

---

