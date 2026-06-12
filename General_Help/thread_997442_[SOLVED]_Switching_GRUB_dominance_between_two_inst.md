---
title: "[SOLVED] Switching GRUB dominance between two installations"
date: 2008-11-29
forum: General Help
---

### Post by TheForkOfJustice on 2008-11-29
I have two Gutsy installations.

The second installation (my backup) took GRUB control away from my primary installation so I have to boot into the secondary if I wish to update GRUB.

Is there a way for my main installation to regain dominance over GRUB so I won't have to do this dance anymore?

---

### Post by jimmy the saint on 2008-11-29
I'm not 100% sure about this, but it seems to me that if you created a symlink from the grub menu.list file in the one that works to the one that doesn't, then you would be able to modify the one in the installation that does not have precedence, and the grub that does would, by extension, be using that one.  

I just read that and it made my head spin, but I think a symlink seems like an easy answer.

---

### Post by falcon61102 on 2008-11-29
If that symlink doesn't work, you could re-install the GRUB and point it towards the menu.lst you want to be used.

Open a terminal and type:
```
sudo grub
find /boot/grub/stage1
```

Being that you have two installs, you should get two results, such as: 
```
(hd0,0)
(hd0,1)
```

For the next two steps, make sure you use the partition with your primiary install on it.
```
root (hd0,0)
setup (hd0)
```

Then restart.  That should redirect the GRUB to use the menu.lst on your primary install instead of the recovery.

---

### Post by TheForkOfJustice on 2008-11-30
Thanks, that did the trick.  Still had to do some editing but at least I can do it from my main partition for once.

---

### Post by falcon61102 on 2008-11-30
Glad that worked out for you.

Be sure to marked the thread solved.

---

