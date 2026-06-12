---
title: "Upgrade from ubuntu 9.10RC to studio? will i get any issues?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by dado023 on 2009-10-25
Hi there, 
let me cut to the chase:
I have isntalled ubuntu9.10RC [COLOR=Red]wubi[/COLOR](inside windows), but i want ubuntu studio,
should i only search in package manager for packages "ubuntustudio" and install those, or form ppa or something?

i am a beginner, please don't tell me "you shouldn't use wubi", i know that :)

i need to know will installing ubuntu studio screw up current ubuntu installation [COLOR=Red]***since the kernel is different***[/COLOR], at leas that is what i read somwhere in the forums when i searched for this post....

waiting for your response, before taking any steps
thanks in advance

---

### Post by earthpigg on 2009-10-25
the best answer to your question that anyone could give, i think, is this:

yes, you may have issues. no one can guarantee issues will not arise. back your important data up and give it a shot.

---

### Post by dado023 on 2009-10-25
> **earthpigg said:**
> the best answer to your question that anyone could give, i think, is this:

yes, you may have issues. no one can guarantee issues will not arise. back your important data up and give it a shot.

yes, i am aware taht i might have issues, that why i am asking about it, i appreciate your  answer because in my last install(same combination 9.10rc..etc) i ticked everything that had "ubuntustudio"  in synaptic pcg manager, then after i rebooted i got kernel panic....

i want to know if anybody has some expirience with this particular upgrade(to studio addons), which one of ubuntustudio packages  i shouldn't install on my current ubuntu to avoid problems?


BTW: how much ram your linux(lxde) sucks on start?....my current ubuntu 9.10RC consumes approx 150MB at start(when logged in)

---

### Post by earthpigg on 2009-10-25
60, give or take. there is no 9.10 release yet, though, due to some difficulties with upstream changes.

> i ticked ***everything*** that had "ubuntustudio" in synaptic pcg manager, then after i rebooted i got kernel panic....

the part i bolded very well may have been your problem :D

this can happen when installing packages that add kernel modules or change the kernel.

different packages may do different things to the kernel, perhaps two or more of them tried to do something at the same time that where not compatible with each other?

if that happens in the future, try a different kernel from the GRUB menu.

when installing ubuntu studio, pick ***one*** of these meta packages at a time and install it.

[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

reboot to allow any kernel changes to take place, or for any kernel modules to be installed and activated. then move on to the next.

none of that is needed for individual userland apps, but with software that makes low level kernel changes the safest thing is to do things incrimentally and reboot in between. this also applies for uninstalling them later.

---

