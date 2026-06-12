---
title: "Update Problem"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by yildiz.a on 2009-04-04
This is error message which is sent by update manager :


"Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead."

What is the problem? Thanks...

---

### Post by bapoumba on 2009-04-04
Please go to Administration > Software Sources and uncheck the cdrom :)

---

### Post by yildiz.a on 2009-04-04
Ok, thanks your advice. It works but I disabled some properties. What will happen if I dont enable them? Why am I taking error messages? Because I tried once updating mounting Ubuntu 8.10 CD and again same error occured. Is it because system fault?

---

### Post by bapoumba on 2009-04-04
If you use the cdrom, you need to check it in Software Sources.
If you do not use the cdrom, uncheck it, that should be it.

---

