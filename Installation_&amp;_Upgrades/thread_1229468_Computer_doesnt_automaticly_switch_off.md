---
title: "Computer doesnt automaticly switch off"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Konopa on 2009-08-02
Installed Ubuntu last night, I was using it and all, then i click turn off, after doing this the pc produced 4 or 5 quick short beeps then comes to a black screen saying system halted and then i have to switch pc off using button, any ideas why? 
I noticed on startup it says something like no dmi bois year..........something i required to enable acpi.

Help :(

Thanks

Pc is a HP 7865 that had new cpu, new ram. I checked ram and it seems ok...maybe updated bois is needed..bois shows 2001
Adding acpi=forcr on kernal line didnt work...seems to delete itself when i go back to it.

---

### Post by Konopa on 2009-08-02
fixed it, new problem now, 3 beeps when turning off still and when pc booting up, screen that displayes system things, says like OK for different sections, one says failed, how do i view this? sorry about not knowing name.

---

### Post by Herman on 2009-08-02
:D I'm not sure about yours, but I just fixed my old computer which had similar symptoms. All mine needed was a new BIOS battery. Now it's working as good as new again. 

To view boot-up log,
```
dmesg > boot.messages
``` or
```
cat /var/log/bootstrap.log
```

---

