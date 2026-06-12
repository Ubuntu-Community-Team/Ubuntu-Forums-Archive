---
title: "Windows partition mouns every time I boot"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-01-13
Every time I boot linux my windows partition mounts automatically. I don't want it to. How do I stop it? 

It started happening after I followed item number 2 off of this site:
[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

How do I undo that?

---

### Post by chrisgibbs on 2008-01-13
Gday,

This one should be easy to sort out.

from console (probably make a backup of fstab first though):


```
sudo gedit /etc/fstab
```


Remove the entry for your NTFS HD

IE the line that would look similar to the one below

/dev/  /media/  ntfs-3g defaults,locale=en_US.utf8 0 0

Restart and it should not be mounted automatically anymore.

Cheers,

---

