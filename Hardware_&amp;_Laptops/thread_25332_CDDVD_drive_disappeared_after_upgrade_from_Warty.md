---
title: "CD/DVD drive disappeared after upgrade from Warty"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by knipknap on 2005-04-09
I recently made the upgrade from Warty to Hoary. It all looked fine, but today I noticed that my CD/DVD drive does not work anymore.
The drive is still plugged on the secondary controller, but the /dev/hdc file disappeared. No information appears in dmesg (it just checks ide0... ide1... ide2... and does not find anything except the hard disk on /dev/hda). (sorry, I currently have no mouse so no copy & paste from the terminal, but believe me, it is not mentioned ;) )

The kernel modules ide_cd, ide_generic, ide_disk, ide_core, cdrom are all loaded according to lsmod, and ide_cd and ide_generic are show unused.

Any idea?

---

