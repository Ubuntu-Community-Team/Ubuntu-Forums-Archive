---
title: "With ati module CPU fan always on"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by songochain on 2007-01-13
Hi i've a problem with dapper, edgy and feisty. If i use ati or radeon in xorg.conf cpu fan is always on but if i use fglrx this doesn happen. Also i've tried to disable acpi but i lose cpu scaling...
I've a radeon mobility 9700 on a amd64 mobile 3200+, running edgy i386 with a 2.6.19 compiled kernel
Thanks

---

### Post by spaci76 on 2007-01-13
hi

please try aticonfig --lsp and paste.

cu
spaci76

---

### Post by songochain on 2007-01-13
Here's:
```
Error: Unable to obtain POWERplay information.
```
Thanks

---

### Post by spaci76 on 2007-01-13
hi,

is beryl on?? in this case the ati powersave tool is out and the ati runs in the highest mode.  
start the defaut session and try the command again.
 
cu spaci76

---

### Post by mxt on 2007-02-24
Same notebook (Asus A4K) and same problem here !

---

### Post by mxt on 2007-02-24
As songochain said, aticontrol doesn't give information about power modes, probably because fglrx is not loaded..

---

