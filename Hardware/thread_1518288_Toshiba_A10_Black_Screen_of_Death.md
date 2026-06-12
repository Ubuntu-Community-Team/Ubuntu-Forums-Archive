---
title: "Toshiba A10 Black Screen of Death"
date: 2010-06-26
forum: Hardware
---

### Post by keithclark on 2010-06-26
I have a Toshiba A10 with an Intel graphics chipset and am getting the dreaded black screen of death upon startup.  This is an upgrade installation to Ubuntu 10.04.

I've found solutions on the net that require the 10.04 CD and using i915.modeset=0 xforcevesa solution, by my CD drive died some time ago and I'm just upgrading as new release come out by downloading them.

Here are the specs for the machine:

[http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=1911&part=1532#spectop](http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=1911&part=1532#spectop)

I can get the machine to boot up into Gnome by using Recovery Mode and using the gnome low graphics mode.  This works fine, but is a pita.

Any help would be appreciated.

Keith

---

### Post by keithclark on 2010-06-26
I found the solution:

Modify /boot/grub/menu.lst
add i915.modeset=1 go your kernel line.

ie:

was: kernel /boot/vmlinuz-2.6.32-22-generic root=UUID=a1b721(more numbers) ro quiet splash

now: kernel /boot/vmlinuz-2.6.32-22-generic root=UUID=a1b721(more numbers) ro quiet splash i915.modeset=1

---

