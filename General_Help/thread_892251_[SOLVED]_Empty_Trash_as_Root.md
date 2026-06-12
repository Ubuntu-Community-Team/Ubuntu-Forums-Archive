---
title: "[SOLVED] Empty Trash as Root"
date: 2008-08-17
forum: General Help
---

### Post by Unanimated on 2008-08-17
I recently downloaded Pekwm, and realized I don't want it. I put it in the trash can in the bottom right of the screen, then hit Empty Trash. The folder and some files are still in there. When I click one of them and hit delete, it says permission denied. This leads me to believe that I need to be root to delete these files. How can I go into the trash as root?

Also, ~/.Trash doesn't exist in my home folder.

---

### Post by aysiu on 2008-08-17
Press Alt-F2 and paste in the command ```
gksudo nautilus
``` I believe your trash is in /home/*username*/.local/share/Trash/files

---

### Post by wilbbe01 on 2008-08-17
According to.....
[http://ubuntuforums.org/showthread.php?t=233569](http://ubuntuforums.org/showthread.php?t=233569) post number 4.

it is located here

~/.local/share/Trash

---

### Post by Unanimated on 2008-08-17
That's where it was. Thanks!

---

