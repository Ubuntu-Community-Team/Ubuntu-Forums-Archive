---
title: "boot help"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by goutty on 2009-03-15
Hi,
I have ubuntu 8.10 installed in dual boot configuration with windows vista.
While booting my laptop shows the following operating systems alongwith windows:-
ubuntu 8.10,kernel 2.6.27-12-generic
ubuntu 8.10,kernel 2.6.27-12-generic(recovery mode)
ubuntu 8.10,kernel 2.6.27-11-generic
ubuntu 8.10,kernel 2.6.27-11-generic(recovery mode)
ubuntu 8.10,kernel 2.6.27-7-generic
ubuntu 8.10,kernel 2.6.27-7-generic(recovery mode)
ubuntu 8.10,memtest 86+


Can anyone tell me why it is showing so many ubuntu installed intead of just 2 for ubuntu.....
I always keep my system update by the update manager.
Will there be any problem if I uninstall ***_[COLOR="DarkRed"]ubuntu 8.10,kernel 2.6.27-11-generic and ubuntu 8.10,kernel 2.6.27-7-generic[/COLOR]_***
from _synaptic package manage_r????

---

### Post by king_lear on 2009-03-15
Its perfectly ok to delete the old kernels.
Its also a good way to free some disk space. Also you must be sure that the kernel you wish to retain is stable on your computer

---

### Post by panmoto on 2009-03-15
It's OK to un-install older kernel. I suggest you keep two latest kernels. Just to make sure the latest kernel is stable for your system, if not you can always go back to the older kernel(s).

But if you just want to make the older kernels not shown but still have them on your PC, you can use Startup-manager application to limit number of kernels shown in grub.

install Startup-manager via synaptic package manager.

---

