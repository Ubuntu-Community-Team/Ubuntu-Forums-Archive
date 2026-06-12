---
title: "Windows partition showing up on Desktop... sort of... I think... idk if I can remove"
date: 2008-07-11
forum: General Help
---

### Post by Redrazor39 on 2008-07-11
The screenshot is attached. My windows partition shows up on my desktop, but not in the desktop folder in nautilus. If I drag it to the trash, it asks if I want to delete it all, and all my important windows stuff is there.

Help? How can I get rid of this icon but still keep my partition untouched?


:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by damis648 on 2008-07-11
> **Redrazor39 said:**
> The screenshot is attached. My windows partition shows up on my desktop, but not in the desktop folder in nautilus. If I drag it to the trash, it asks if I want to delete it all, and all my important windows stuff is there.

Help? How can I get rid of this icon but still keep my partition untouched?


:confused::confused::confused::confused::confused::confused::confused::confused:

Ubuntu will automatically show mounted partitions on the desktop and they will not show in the desktop folder. You can unmount it (Right click, unmount) or add it to the fstab.

---

### Post by Redrazor39 on 2008-07-11
It used to only show up in the file browser...

wait.... I get it now

I accidentally clicked on it and entered my root pass b/c I wanted to see what was in it, but it's still on the desktop.

Tell me, if I unmount it, will it still show up in the file browser side pane or will I have to use the command line (i dont know the command)

---

### Post by damis648 on 2008-07-11
> **Redrazor39 said:**
> It used to only show up in the file browser...

wait.... I get it now

I accidentally clicked on it and entered my root pass b/c I wanted to see what was in it, but it's still on the desktop.

Tell me, if I unmount it, will it still show up in the file browser side pane or will I have to use the command line (i dont know the command)

Mm... I do not know. Sorry. Try it and you will see. If it is not, reboot.

---

### Post by eelensar on 2008-07-11
Right-click on it and click "Unmount". It will still be available in Nautilus in the left hand sidebar and if you browser to "Computer". Clicking on it in either of those places will mount it again. No need for the command line. I do the same with my flash drives often.

---

### Post by Redrazor39 on 2008-07-12
Ok I rebooted. Thanks for the info and now it's fixed. I understand that when I mount it it shows up on the desktop


yay :)

---

