---
title: "View process report on startup"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by steddy on 2009-08-04
Hi,
I can't see the list of processes during ubuntu bootup (my screen is black until the authentication form).
Now I have a problem with the kernel upgrade (2.6.28 won't start) so the process list must be usable to identify the problem.
Thanks

---

### Post by steddy on 2009-08-04
I've found it.
I have to remove the words 'quiet splash' from the row corresponding to the current kernel in '/boot/grub/menu.lst'

---

### Post by kayvortex on 2009-08-04
Do you mean the boot-up process when you say "list of processes" , or the grub menu (the thing where you can choose what OS to boot)?

Edit: sorry, you beat me too it. Yes, deleting "splash" removes the splash screen. Just be aware that any kernel updates will now bug you about a "locally installed menu.lst" or something similar. Just select the option to install the "package maintainer's version" or "merge" the versions (keeping the "locally installed one" will not give you the option of booting the new kernel version, if I remember correctly).

---

