---
title: "[SOLVED] Dirty GRUB"
date: 2008-07-18
forum: General Help
---

### Post by timswait on 2008-07-18
It's working fine, but often when I install an upgrade it adds an extra entry to my GRUB boot up screen. I now have about 8 Ubuntu 8.04 and associated recovery modes listed in my Boot menu. It's a little irritating, they all seem to do the same thing when I click them, so how do I get rid of all but one of them?

---

### Post by Potatoj316 on 2008-07-18
in a terminal type sudo gedit "/boot/grub/menu.lst" (no quotes) then scroll all the way to the bottom and you will see blocks of approx. 5 lines.  Each block is an entry on your GRUB boot screen.  They are in the same order here as in the grub screen.  You can reorder them or delete them.  Just make sure to move or delete the whole block.

The difference between them is the kernel version, it is safe to delete as long as you do not care (you probably dont) to ever use an older kernel.

---

### Post by timswait on 2008-07-18
Thanks mate, that's better:)

---

### Post by drs305 on 2008-07-18
For future reference, there are other ways to handle this as well.

One way is to remove the extra (older) kernels via synaptic. Search for  'linux-image' The kernels installed on your machine will look like "linux-image-2.6.24-19" or "linux-image-2.6.24-19-generic". Keep at least the one you are using and an older one you know works. Any kernels you remove from synaptic will also automatically be removed from your menu list.

Removing the items via the grub menu as you have done leaves them on the machine, which is perhaps what you want. A safer method than manually editing the menu.list is to install startup-manager, which will allow you to display how many kernels you want to view, how long to display the menu, which kernel or OS to boot from, and a lot of other information.

You can read more about it here:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

To install StartUp-Manager:
```
sudo aptitude install startupmanager
```

To run: System, Administration, StartUp-Manager

There a lots of ways to do things in ubuntu. These are just a couple of extra options.

---

### Post by bodhi.zazen on 2008-07-18
IMHO it is best to just remove the previous kernels.

Always keep at least one old kernel for backup.

Other solutions are just cosmetic and leave the old kernels on your hard drive as junk (unused material), not that they are all *that* large, but still, if you are not using them why not remove them ?

---

