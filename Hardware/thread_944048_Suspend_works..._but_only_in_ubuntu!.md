---
title: "Suspend works... but only in ubuntu!"
date: 2008-10-10
forum: Hardware
---

### Post by tmafcerqueira on 2008-10-10
Hey there,
I've used arch and debian before on this laptop, and decided to install ubuntu just to check if suspend to ram worked. And it does:eek:
The problem is that I have no idea why! I mean, I googled for days in arch and debian to find something, xorg configs, applications to suspend, scripts to execute, etc. I finally got hibernate to work(but the USB mouse would work after booting) but never got to have suspend working. As I installed ubuntu it worked out of the box. Now...
Does anyone know what configs or applications are used to suspend in ubuntu? What about the kernel? Is it the standard for every other distro or has canonical applied some patches to make suspend work on some hardware?
Thanks in advance, I would love to get suspend to work in slackware (the next distro to go on this laptop)
Oh, btw! Something that I forgot to mention. Suspend worked on the other distros... The computer would go into low power mode, the light would even switch to brown(which means the laptop is suspended). The problem is that the computer wouldn't boot back up. It would just freeze, with a blank screen. I looked up xorg.conf problems but nothing seemed to surface

---

### Post by kerry_s on 2008-10-10
suspend depends on the vid driver, ubuntu installs the restricted driver for you. 
so the question is did you use the right drivers for your vid card in the other disto's?

---

### Post by tmafcerqueira on 2008-10-11
Yes, I did. I have a mobility radeon 9200, so I installed the open source "ati" driver. I had compiz enabled in debian and kwin's composite features enabled in arch.

---

### Post by kerry_s on 2008-10-11
okay, how about some info on your computer?

---

