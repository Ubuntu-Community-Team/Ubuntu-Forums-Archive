---
title: "[SOLVED] how can i add fedora to my ubuntu bootloader?"
date: 2008-11-15
forum: General Help
---

### Post by chriskin on 2008-11-15
i recently installed fedora to my laptop and i chose not to add its bootloader as i wanted to keep the ubuntu one because i work mostly on ubuntu and i wanted to be able to customize it more easily.

so , does anyone know which are the lines to add fedora to my grub?
(it is fedora 10 beta)

---

### Post by lswb on 2008-11-15
You can add a boot stanza for fedora to /boot/grub/menu.lst in the same way that the lines to boot ubuntu are present, however there can be some problems with this method. There is good information on this site:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

To just add fedora to the existing ubuntu boot menu, you can edit (as root) /boot/grub/menu.lst but you will need to know how grub sees the fedora partition. The link above does a good job of explaining how to do that.

I like to use a small grub partition and install the boot loader for each distro to the _partition_ for that distro. Then, from the initial grub menu.lst that first runs at boot time, you can add a chainloader statement (as explained in the link) to switch to that partition and OS.

The big advantage of this method when using multiple linux distributions, is that each distribution will be able to update it's own bootloader menu when there is a kernel upgrade.

---

### Post by chriskin on 2008-11-16
thanks for the idea of the chainloader, i will make one right now :)

---

### Post by chriskin on 2008-11-16
your idea worked just fine, (even though fedora is not as good as i hoped it would , back to ubuntu now :))

---

