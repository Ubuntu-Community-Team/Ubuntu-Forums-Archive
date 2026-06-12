---
title: "[SOLVED] No signal? suddenly?"
date: 2008-07-15
forum: General Help
---

### Post by StOoZ on 2008-07-15
everything was ok , used the effects with the nvidia driver enabled (in 'Hardware drivers') , suddenly it crashed , and whenever I try to log in , it goes to 'no signal' mode (the screen).
to fix it , on grub I press ESC >> Fix x server , and then it loads , but still , whenever I enable the nvidia driver , it goes back again (the no signal).

any idea???
:confused::(

using 8.04

---

### Post by phidia on 2008-07-15
What does your /etc/X11/xorg.conf that's running the nvidia driver look like? I'm thinking something must be off in that configure file. 
If you can either boot from the livecd or look for a backup file in /etc/X11 after you fix x and the system is working for you then copy and paste  or attach it here.

---

### Post by StOoZ on 2008-07-15
thanks for the reply.
the problem is solved , weird , it has to be with the PSU.
I changed switched the power connector of the HD to the GFX card and all is fine now.
weird

---

