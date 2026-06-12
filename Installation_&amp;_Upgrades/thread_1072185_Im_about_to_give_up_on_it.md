---
title: "Im about to give up on it"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by mavrick70004 on 2009-02-17
so here is the issue and a walk through of what i have done.

I have Two Hd, one Sata Hd for my Xp install, and one IDE Hd for ubuntu. I put the ubuntu cd in and reboot computer, load the boot menu and choose to boot from the cd, everything goes fine and i get a brown background and a lil interface for install, i answer all the questions and choose the option to install on my second Hard drive ( the IDE hard Drive ) and it completes install and asks me to reboot. I reboot and i get a option to start windows Xp or ubuntu it is NOT the Grub menu. If i choose Xp then Xp will load and everything works fine, if i choose ubuntu then i get a splash screen that says ubuntu with a move orange bar and it will stay there for a couple min then go black for a min then give me a message that says loading please wait and brings up some "easybox"(i think thats what its called) command prompt or somthingand then im stuck there, i have checked the cd and there r no errors. i am able to boot from the cd and choose "boot from the First Hard Drive" and it will bring up the Gui but it seems sort of slow, i have been trying to do this all day and im about to say F it. Can anyone help?

---

### Post by 3rdalbum on 2009-02-17
Busybox. It generally means that something has gone awry with the boot process. What happens if you type "exit" at the Busybox prompt? (and press Enter). Will it boot then?

If the GUI seems a bit slow, it's likely because you don't have 3D graphics drivers installed. It's nothing to worry about unless it's slow *after* the drivers are installed.

---

### Post by mavrick70004 on 2009-02-17
if i type exit it just drops down a line and gives me a blinking line

---

