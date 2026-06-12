---
title: "MSI Wind and Clickable Trackpad"
date: 2009-02-10
forum: Hardware
---

### Post by mtorbin on 2009-02-10
Hey folks,

This issue has been posted before at [http://ubuntuforums.org/showthread.php?t=425430](http://ubuntuforums.org/showthread.php?t=425430) but the file that is referenced there isn't in my etc dir.  I just installed 8.10 and I would LOVE to get rid of the clickable trackpad.  Any help would be much appreciated.

Thanks,

 - MT

---

### Post by mtorbin on 2009-02-10
Is the file I'm looking for even called xorg.conf or is there another file I should look for?

---

### Post by Th3Sourc3 on 2009-02-12
Make sure you're doing a capital X in the X11 part.  It's case-dependant.  

/etc/X11/xorg.conf is different from /etc/x11/xorg.conf

Definitely create a backup of the file, as well.

EDIT: By the way, you're probably going to want to access the file via a terminal anyway, so try that first.

gksudo gedit /etc/X11/xorg.conf from terminal is better than just trying to use the file manager to navigate over to the file.

---

### Post by mtorbin on 2009-02-12
> **Th3Sourc3 said:**
> Make sure you're doing a capital X in the X11 part.  It's case-dependant.  

/etc/X11/xorg.conf is different from /etc/x11/xorg.conf

Definitely create a backup of the file, as well.

EDIT: By the way, you're probably going to want to access the file via a terminal anyway, so try that first.

gksudo gedit /etc/X11/xorg.conf from terminal is better than just trying to use the file manager to navigate over to the file.

Thanks, I found the file but mine doesn't quite look like the others being referenced here.  I did add the line but it doesn't seem to jive (along with other inconsistencies).  I wonder if the Wind doesn't play nice with 8.10.

---

