---
title: "problem with trash: the system crash"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by ubunlilluz on 2009-05-26
hi,
after installing the 9.04 unfortunable i've noticed that i've a problem with the Trash: when i try to empty, the entire system crash, the mouse cursor stops in the screen, the keyboard doesn't work too and the only thinh i can do is unplug and plug the pc to reboot it. I tried to empty the trash by nautilus and by terminal too, but the results are always the same, the system doesn' work anymore and i've to unplug and plug to restart.
Nobody can help me?
thanks

---

### Post by ubunlilluz on 2009-05-26
i've choosen the ext4 file system, maybe the problem is there

---

### Post by javyn999 on 2009-05-31
I have this same problem, but only when I empty large files over 1 gb from the trash.  I am running on ext4 as well.

---

### Post by nakedfanatic on 2009-06-12
I also have this problem, and I also am using ext4.

I even tried to delete the trash files from the shell:

rm -rf ~/.local/share/Trash/*

and this also crashed the entire system.

---

