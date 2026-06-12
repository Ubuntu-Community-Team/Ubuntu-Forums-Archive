---
title: "newbie install problem"
date: 2005-01-27
forum: Installation &amp; Upgrades
---

### Post by preston on 2005-01-27
i seem to be having a problem, my install from xp to ubuntu went well until i rebooted. i got a message stating that gdm config had failed and as a result x server was disabled and that i should see xfree86.org. forgive me if ive missed the obvious any info would be apreciated and feel free to ask for more info. oh and please the more detailed the better thanks

---

### Post by albersag on 2005-01-27
[QUOTE=preston]i seem to be having a problem, my install from xp to ubuntu went well until i rebooted. i got a message stating that gdm config had failed and as a result x server was disabled and that i should see xfree86.org. forgive me if ive missed the obvious any info would be apreciated and feel free to ask for more info. oh and please the more detailed the better thanks[/QUOTE]
 Try on shell, entering with your login password created on installation steps,

sudo dpkg-reconfigure xserver-xfree86

Choose vesa driver, i always works, then choose the correct driver for your graphics card

---

