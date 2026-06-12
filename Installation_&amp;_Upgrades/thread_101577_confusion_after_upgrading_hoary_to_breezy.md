---
title: "confusion after upgrading hoary to breezy"
date: 2005-12-10
forum: Installation &amp; Upgrades
---

### Post by porsher_puddles on 2005-12-10
i upgraded my ubuntu hoary to breezy from the cds that arrived all is well everything still works fine. it installed using the default 386 kernel.
now i had already upgraded the hoary to 686 kernel to suit my setup better,this i did via synaptic, and i resetup my xserver and hoary was fine.
when i visit synaptic now it still has 686 kernel installed for hoary so i can't seem to find a way to upgrade kernel for breezy appart from compileing manually which makes me nervous. what would be the best thing to do here, or should i say the easiest, should i uninstall all the kernals i'm not using in synaptic , would i be able to set up 686 kernel for breezy then?

---

### Post by MartinG on 2005-12-10
If you've got your sources.list pointing at the breezy repositories, then after updating synaptic will show you the current kernels for breezy (2.6.12-10-686 is listed on my computer), and you can update as normal.

What do you mean by saying the hoary 686 kernel is installed?  How do you know it's not current for breezy?  AFAIK 2.6.12-10-686 is not unique to breezy or hoary.  If it shows up in synaptic as installed, then it will upgrade as above.  It's only if it shows up in installed (local or obsolete) that you need to be a bit more cautious.  In that case install the current kernel and make sure it boots before deleting the old one.

Hope that helps.

---

### Post by porsher_puddles on 2005-12-10
i'm a newbie so i'm not really good at explaining whats wrong, but my grub looks like this. it has the default kernel which installed with breezy on the top of the list (386) then the recovery one, then kernal 2.6-10-6-686 which boots but hangs on shutdown, then another kernal i used in hoary 2.6-10-5.686 which comes up if i try to load with kernal panic error.
i think the problem is i still have my repos pointing at hoary and not breezy how do i change this?

---

### Post by dcstar on 2005-12-10
[QUOTE=porsher_puddles]
......
i think the problem is i still have my repos pointing at hoary and not breezy how do i change this?[/QUOTE]
Go into Synaptic-Settings-Repositories and edit each Ubuntu one, manually changing any "hoary" you find to "breezy".

It may take you a little while, but it should help.

---

