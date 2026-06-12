---
title: "inspiron 6000 (xorg?) issues"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by tehsyco on 2005-08-12
Hi all,
 
  I just installed the latest Hoary on my Dell Inspiron 6000 and am having a problem every time it starts up. It boots up and goes into xorg and my screen becomes completely black. I have no idea what this could be a problem with as I'm getting no error whatsoever. Did anyone have this issue on an inspiron 6000? Any xorg.conf files you guys can post might be helpful and I'd greatly appreciate it.

Thanks,
Jordan

---

### Post by tehsyco on 2005-08-12
appears to be fixed now by switching to different video settings. i'm still having a problem using intel 2200 networking card to connect to inet, suggestions?

---

### Post by firestrife2382 on 2005-08-12
I'm having same issues with display, umm how exactly did you get this fix?

---

### Post by tehsyco on 2005-08-12
Don't use the i810 display - I believe it's called vesa in the list, I just switched to that and it worked.

---

### Post by firestrife2382 on 2005-08-13
i dont see that during the setup, i only see is selection for resolution.

---

### Post by s_p_a_r_k_y on 2005-08-13
firestrife, manually edit /etc/X11/xorg.conf

look for i810 and then change it to vesa

---

### Post by varunus on 2005-08-13
Eew.  The vesa driver should not be used.  You'll start to notice things like having no OpenGL, and windows lagging while you drag them, and all sorts of things.

You said the i810 driver doesn't work for this laptop?  Can you, when in vesa mode, type lspci into a terminal and post the output here?  Most i810 problems can be fixed...Also, can you try a boot with the i810 driver, let it fail, and then change to vesa, boot into GUI, and post the /var/log/Xorg.0.log.old file here?

---

### Post by halcion on 2006-02-01
I am also having a great deal of problems with the same system, the 1680x1050 version with the 915GM chip. The system boots normaly and then the xwindow system starts and the screen stays black. I get a tribal drum noise when it first happens and if i press enough buttons it makes the noise again. I have tried FC3&4, Mandrake 10.1 and i get the same sort of problem.

Any help or advice, im only trying to this out so i can make sure i get something i have to do at work right the first time and its anoying to be beaten by a peice of code.

---

### Post by alamba on 2006-02-01
Same problem here. Same solution here. i915GM chipset, but seems to work fine with the i810 driver in 5.10. Since I upgraded from 5.04 via apt-get I don't have that driver yet. Anyway to upgrade just the i810 driver?

Akshay

---

