---
title: "x11 configuration is whacked I need help!"
date: 2008-09-06
forum: General Help
---

### Post by Cr0n_J0b on 2008-09-06
So, i just went through and swapped my server from on motherboard to another.  In the process, most everything came back, but the x server isn't booting.  I get popped down to the text mode when I boot up.  I tried copying the xorg.conf.failsafe file to xorg.conf to see if that would boot, but it just hung when starting x.  Is there anything else I shoudl try before I reload from scratch?

thanks

---

### Post by cdtech on 2008-09-06
Try running in text mode:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Cr0n_J0b on 2008-09-06
Thanks so much.  It worked perfectly!!!

I really appreciate the help.

---

### Post by cdtech on 2008-09-06
Your welcome....

---

