---
title: "touchpad working in precompiled kernel but not in mine"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by asterix404 on 2005-10-08
I needed to recompile my kernel in part becasue I really just wanted to but also to see just how hard it would be to get it working on my laptop. I have litterally gone though every compiled in option and modual that gets loaded at boot time one at a time and compiled it into my kernel. I am all out of ideas and am very frustrated. I am not exactly new to linux but I really don't mess around with this stuff if I have to, and I did since it installed about a million modules and I don't want to go through each one of them and pick and choose which ones I want. Basicly can someone please help me get my mouse to work... my built in keyboard works fine and I compiled that option in to the kernel. I also have the Mice[*] ps/2 [*] checked as well as the /dev/psaux default. Thanks a lot, ~Ben

---

### Post by ranf on 2005-10-09
[QUOTE=asterix404]Basicly can someone please help me get my mouse to work... my built in keyboard works fine and I compiled that option in to the kernel. I also have the Mice[*] ps/2 [*] checked as well as the /dev/psaux default.[/QUOTE]
If it is a PS/2 just try:
```
sudo modprobe psmouse
```

---

### Post by asterix404 on 2005-10-09
Thats the thing though... I compiled that into my kernel not as a modual. The psmouse is what the default kernel loads but the best part about it is that I commented out both the modules that get loaded by the kernel and the mouse still works in hte default....

---

### Post by ranf on 2005-10-10
[QUOTE=asterix404]Thats the thing though... I compiled that into my kernel not as a modual.[/QUOTE]
Statically linked? Only psmouse or mousedev also? (I don't know how the kernel config parameters are named)

[QUOTE=asterix404]The psmouse is what the default kernel loads but the best part about it is that I commented out both the modules that get loaded by the kernel and the mouse still works in hte default....[/QUOTE]
You commented out psmouse and mousedev in /etc/modules?

---

