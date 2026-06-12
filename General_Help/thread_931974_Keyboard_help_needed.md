---
title: "Keyboard help needed"
date: 2008-09-27
forum: General Help
---

### Post by crimsongrim on 2008-09-27
As of right now i am using the Dvorak layout, but when i have to login i have to use QWERTY. Can anyone tell me how to fix that?

---

### Post by y-lee on 2008-09-27
Interesting question and as i Have to admit that i don't use dvorak I have no way of testing this.

But from what i [just read]("http://doomtech.net/wiki/index.php/Dvorak_Simplified_Keyboard#Linux") online you need to edit your xorg.conf file and change Option "XkbLayout" to

```
Option "XkbLayout" "dvorak"
``` 

Note **back up** this file before you edit it just in case and note you have to be superuser to edit it. So if you use gedit, to edit the file:

```
gksudo gedit /etc/X11/xorg.conf 
```

make the reguired changes and save and exit gedit.

Reboot and hope it works :)

---

