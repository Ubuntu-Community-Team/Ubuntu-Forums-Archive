---
title: "Run out of space in some shape or form."
date: 2008-11-07
forum: General Help
---

### Post by sandbag the great on 2008-11-07
I'm a very recent convert to ubuntu from windows and aint that teched up so be gentle.

I think some how I've run out of room in my desktop folder or perhaps the ubuntu partition on my hard drive. My suspicion is its the latter because when I intalled ubuntu, at the section where you move the dial to select how much of your drive you want to section off, I think I moved it to something stupid like 85 -90% expecting this to be how much room would be provided for ubuntu. I have two hard-drives built into my system both with 160gb of space and only one has stuff on it (and then only about 20g perhaps) so there is technically plenty of space left in my machine. in an ideal world I would of liked to keep ubuntu on one hard drive and dual boot windows from the other but I wouldn't know where to start doing this.

My problems started when i changed some settings in firefox, at which point the back button and the search engine on the browser stopped working. Second thing i noticed was when i press the quit (ubuntu) button all my panels automatically dissapear and I can only quit by bringing the console up. Thirdly I'm pretty much getting errors when i start up any program now, such as;

open office;

open office.org could not save important internal information due to insufficient free disk space
/home/shaun/.openoffice.org2/user/backup

Amarok

there was an error setting up inter-process communications for KDE. the message returned by the system was;
could not read network connection list home/shaun/.DCOPserver_shaun-desktop_0


any help in allocating more room to ubuntu or even my whole second hard-disk would be greatly appreciated. (searched and can't find the help I need)

---

### Post by dcstar on 2008-11-08
> **sandbag the great said:**
> I'm a very recent convert to ubuntu from windows and aint that teched up so be gentle.

I think some how I've run out of room in my desktop folder or perhaps the ubuntu partition on my hard drive. 
........
any help in allocating more room to ubuntu or even my whole second hard-disk would be greatly appreciated. (searched and can't find the help I need)

In a terminal:

```
df -h
```

If your "/" partition say 0% available, then do things like removing cached packages in Synaptic and emptying the /tmp folder.

Do a search for "root partition full".

---

