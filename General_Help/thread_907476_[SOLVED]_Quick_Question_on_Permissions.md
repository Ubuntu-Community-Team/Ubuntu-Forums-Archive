---
title: "[SOLVED] Quick Question on Permissions"
date: 2008-09-01
forum: General Help
---

### Post by opothehippo on 2008-09-01
Hello.

I just recently upgraded to Hardy, and my touch pad didn't work (M1530). I read the support forums and learned that the fix was to add i8042.nomux=1 to the GRUB menu while booting. This works perfectly for me, but I wanted to make it permanent, by editing /boot/grub/menu.lst. I open up menu.lst and edit the correct line, but it says that I don't have the correct permissions to edit it. I'm the only account on my computer, and I know my password, I just dont know where, how, or if there is a certain command I need to know. Can you peoples help me?

[SIZE="1"](And sorry if this has already been answered or is the wrong section.)[/SIZE]

---

### Post by jerome1232 on 2008-09-01
You need to edit it as root

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by opothehippo on 2008-09-01
Thanks, it worked very well.

---

