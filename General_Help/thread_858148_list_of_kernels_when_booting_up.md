---
title: "list of kernels when booting up"
date: 2008-07-13
forum: General Help
---

### Post by thedon_1 on 2008-07-13
I am running an Ubuntu/ Vista dual boot set up and when i start the PC grub has many ubuntu kernels.

I am assuming these are older versions and i no longer need them. How do i clear these?

Thanks

---

### Post by Vishal Agarwal on 2008-07-13
Because of these New kernels I need to edit my menu.lst again and again. Also I don't know what to do with the old versions of kernels.

---

### Post by WRDN on 2008-07-13
In the terminal, type:

```
sudo gedit /boot/grub/menu.lst
```

This will allow you to edit the menu.lst file with root privileges.

Now, find the line "howmany=all" (the one with a single # before it) and change it to "howmany=1".

This will ensure, regardless of kernel updates, only 1 kernel entry appears in the GRUB menu.

This process can also be done in a UI with Startup-Manager (in Synaptic).

---

