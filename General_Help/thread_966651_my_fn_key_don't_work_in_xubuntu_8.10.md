---
title: "my fn key don't work in xubuntu 8.10"
date: 2008-11-01
forum: General Help
---

### Post by Ioky on 2008-11-01
I have a Toshiba Portege M100, it usually work beautifully with xubuntu out of the box. But when I did a clean installation, my fn key no long work. 

I try to install fnfxd but I get this error message. 

fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel). 

Is there anything I can do to get my fn work?

---

### Post by pooyaplus on 2008-11-01
Try this command and see if it returns the key number when you press the fn key
```
xev
```
If it return the number, the key is just working. And maybe you need to define the key combinations again.

---

### Post by Ioky on 2008-11-01
NO, none of the Key works

Any Idea what is going on?

---

### Post by Ioky on 2008-11-01
Now I try 

modprobe toshiba_acpi

it say: FATAL: Module toshiba_acpi not found 

is there anywhere that I can add this Module to my knecel in ubuntu.

---

### Post by pooyaplus on 2008-11-02
If you got a Phoenix Bios, you may update to the latest Bios version form the Toshiba website. See if that helps.

The kernel modules to be loaded at boot time are listed in this file:
```

/etc/modules

```

---

### Post by Ioky on 2008-11-02
I have the ACPI BIOS and I can't found the module directory

---

