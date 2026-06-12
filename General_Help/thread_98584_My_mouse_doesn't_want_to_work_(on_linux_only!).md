---
title: "My mouse doesn't want to work (on linux only!)"
date: 2005-12-03
forum: General Help
---

### Post by SkillZero on 2005-12-03
ok guys, here it is, new thread.
i bought a new mouse, because the other one kinda screwed up.
since i installed it , it didn't work, a PS/2 mouse.
i tried to edit my xorg.conf file, and change the mouse section to PS/2 or to Auto.
i tried to reconnect the mouse.
i tried to check in device manager, there was no mouse section.
i tried to do "sudo cat /dev/input/mice".
i tried to type "lsmod |grep psmouse" it gave me "psmouse 26116 0".
i tried to add a "psmouse" line to my /etc/modules file.
i tried to check if the mouse is damaged, its not!

[my xorg.conf file.]("http://rapidshare.de/files/8286666/xorg.conf.html")

plz, is there anything i didn't try and might help me?

---

### Post by SkillZero on 2005-12-04
ok...tnx alot =\
*cough*help*cough*

---

