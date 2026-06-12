---
title: "new 8.10 install"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by alansplace on 2009-02-19
i just installed 8.10.  i thought i was installing it over top of my old mandriva 2007 powerpack, but the bootloader still contains mandriva screen displays.  when i get booted up i have no keyboard or mouse control.
--
Alan :D

---

### Post by Pumalite on 2009-02-19
Boot your Live CD and from the Terminal; post:
```
sudo fdisk -lu
```

---

### Post by alansplace on 2009-02-19
> **alansplace said:**
> i just installed 8.10.  i thought i was installing it over top of my old mandriva 2007 powerpack, but the bootloader still contains mandriva screen displays.  when i get booted up i have no keyboard or mouse control.
--
Alan :Dwell, i answered both questions myself.  the bootloader got written to my windows disk and created a multiple boot system.  wheras my intention was to change between the windows drive and the linux drive (worked with mandriva) in the bios.  oh well.  when i set the windows drive to boot i get the multiple boot menu and when i boot ubuntu i then get mouse and keyboard control.
--
Alan :D

---

