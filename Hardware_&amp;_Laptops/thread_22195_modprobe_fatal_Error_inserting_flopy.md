---
title: "modprobe: fatal: Error inserting flopy"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by milosz on 2005-03-26
Hi, 
i have installed Ubuntu 4.10 on HP Compaq 9020 nx without floppy station. During booting system I see:
> modprobe: fatal: Error inserting flopy (/lib/.../floppy.ko) No such device 
I read [it](http://ubuntuguide.org#modprobefatalerror)  but i'm not sure what i shuld write in my case.
Regards

---

### Post by Phrack on 2005-03-26
If you really don't need the floppy module, you can disable. Edit the blacklist file (*/etc/hotplug/blacklist*) and add the module name at the end.

---

