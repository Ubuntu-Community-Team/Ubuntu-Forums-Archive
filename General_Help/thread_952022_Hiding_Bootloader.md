---
title: "Hiding Bootloader"
date: 2008-10-18
forum: General Help
---

### Post by AlexMono94 on 2008-10-18
Howdy,

Is there a way in which I can autoboot into Vista bypassing the Windows Bootloader and when I want to use Ubuntu, press a key to show the bootloader?

---

### Post by gjoellee on 2008-10-18
Yes I think there is a way but the chance for messing up your bootloader is extremely high, and if you mess up your bootloader you must install OS again (and I guess you don't want to do that)...

---

### Post by wakojakop on 2008-10-18
> **gjoellee said:**
> Yes I think there is a way but the chance for messing up your bootloader is extremely high, and if you mess up your bootloader you must install OS again (and I guess you don't want to do that)...
You dont have 2 ruin your boot loader
1) open your boot.ini file on the root of the HD that you installed windows on
2) Edit the second line 'timeout=30' to say 'timeout=2'
3) save the file

now when you boot, it will sit at the boot menu for 2 seconds before booting vista
if you want ubuntu, select it before the time is up!

---

