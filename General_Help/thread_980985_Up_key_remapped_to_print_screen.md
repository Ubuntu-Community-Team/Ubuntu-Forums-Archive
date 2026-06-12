---
title: "Up key remapped to print screen"
date: 2008-11-13
forum: General Help
---

### Post by shingalated on 2008-11-13
I was just compiling some stuffs in the terminal, and noticed my up key suddenly remapped itself to act as a print screen key.  How could this happen and how can I set it back?

---

### Post by shingalated on 2008-11-13
Also, my media buttons stopped working...now that I think of it this all happened right after I did a apt-get autoremove to clean up my system a bit.

---

### Post by ahocevar on 2008-11-14
I was able to fix both issues by removing my ~/.Xmodmap file. According to the 8.10 release notes, Xmodmap files created with 8.04 or earlier will no longer work.

---

### Post by shingalated on 2008-11-16
I don't have that file unfortunately.  A weird thing happened the other day after a few reboots, my volume/media keys and the up key started working again, but one reboot later and it was back to acting weird again.

---

### Post by shingalated on 2008-11-20
It is still stuck that way :(

---

### Post by pro-rsoft on 2009-03-02
For me, it seems like it's just the latest kernel. When I boot into an older kernel it works fine.

Also, on VMWare this problem is also occurring (even with older kernels).

EDIT: I've found a fix. Execute this in terminal:
gconftool-2 --recursive-unset /desktop/gnome/peripherals/keyboard
Then, restarting X by doing control+alt+backspace worked.

---

### Post by ennay on 2009-07-02
> **pro-rsoft said:**
> 
EDIT: I've found a fix. Execute this in terminal:
gconftool-2 --recursive-unset /desktop/gnome/peripherals/keyboard
Then, restarting X by doing control+alt+backspace worked.

Worked for me, too, thanks!

---

