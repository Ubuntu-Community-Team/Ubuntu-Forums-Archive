---
title: "Edit the dual boot menu"
date: 2008-09-01
forum: General Help
---

### Post by Priest.Lucard on 2008-09-01
In Ubuntu 8.04 how would I edit the dual boot menu to show just one version of Ubuntu and my Windows XP.

---

### Post by Iowan on 2008-09-01
It's been awhile since I edited it, but I suspect you could delete the extra options in **/boot/grub/menu.lst**.

---

### Post by fooman on 2008-09-01
before you go deleting the entries,  play it safe and try just commenting them out first (by placing a # in front of each line.  grub will ignore any lines with # at the beginning).  if all goes well,  you can delete what you like later.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Iowan on 2008-09-01
> **fooman said:**
> before you go deleting the entries,  play it safe and try just commenting them out first (by placing a # in front of each line.  grub will ignore any lines with # at the beginning).  if all goes well,  you can delete what you like later.
Agreed - Or make a backup of the file first```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```... or both.

---

### Post by ad_267 on 2008-09-01
You can also uninstall old kernels that you don't need anymore using Synaptic.

---

