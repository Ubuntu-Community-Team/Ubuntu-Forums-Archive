---
title: "Issue with booting ubuntu in windows"
date: 2008-11-24
forum: General Help
---

### Post by ShirishAg75 on 2008-11-24
Hi all, 
 I filed [lpbug]301670[/lpbug] The basic issue is I get is this after I  try to boot from the wubildr.mbr (bootloader) :-

 **'Error 1: Filename must be either an absolute pathname or blocklist'**

I also see that there are two menu.lst one which is in :-

D:\ubuntu\winboot\menu.lst and the other one at 

D:\ubuntu\install\boot\grub\menu.lst

I also googled and got this thread [http://ubuntuforums.org/archive/index.php/t-372070.html](http://ubuntuforums.org/archive/index.php/t-372070.html) now the comment at the bottom says removing the "savedefault" command works but which of the menu.lst should be used?

---

### Post by bapoumba on 2008-11-24
Moved to Wubi.

---

### Post by ago on 2008-11-25
Replied in the bug report: [https://bugs.edge.launchpad.net/wubi/+bug/301670](https://bugs.edge.launchpad.net/wubi/+bug/301670)

---

### Post by ShirishAg75 on 2008-11-26
hi ago, replied to the bug-report, see if you can find a solution to the same.

---

### Post by roshanjose on 2008-11-29
do one thing.....

just skip the disk checking at booting by pressing ESC..

then when login, open a terminal and type fsck -y...

this will solve your problem

---

