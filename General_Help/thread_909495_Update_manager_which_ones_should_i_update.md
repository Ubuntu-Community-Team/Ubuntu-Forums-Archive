---
title: "Update manager which ones should i update?"
date: 2008-09-03
forum: General Help
---

### Post by viaciofano on 2008-09-03
I have just bought a dell with ubuntu 8.04. when checking for updates via update manager. there is 967 updates. 
looking through there are programs that i do not have?
some programs that i do not want.
some updates that i think might affect my system.
can you help with which ones to update or how i can trim down some of the updates....

can i go back on updating

Vinny

---

### Post by rossjman1 on 2008-09-03
You should install all the updates that are under the "Important Security Updates". The Recommended updates are up to you. I ususally just go with the defaults (some in this category are selected for you, while others are not). You can sort through all these if you wish (I would recommend at least updated the library packages (ones that start with lib). Most of these updates are small and shouldn't break your system.
Any updates listed in this window are updated versions of software you already have.

---

### Post by kostkon on 2008-09-03
> **viaciofano said:**
> I have just bought a dell with ubuntu 8.04. when checking for updates via update manager. there is 967 updates. 
looking through there are programs that i do not have?
some programs that i do not want.
some updates that i think might affect my system.
can you help with which ones to update or how i can trim down some of the updates....

can i go back on updating

Vinny
It would be better if you could install all of them. But to be sure that you are not installing testing packages, go to *System -> Adminstration -> Software Sources* and in the *Updates* tab check that the *hardy-proposed* (*Pre-released Updates*) is not enabled.

---

### Post by Oldsoldier2003 on 2008-09-03
> **rossjman1 said:**
> 
Any updates listed in this window are updated versions of software you already have.
A way to get around this is to uninstall any applications you don't need/want - be careful here though because some have really unexpected dpendencies... then run ```
sudo apt-get update
``` after you have downloaded the new package lists let the updater decide what needs updating and accept them all.

---

### Post by durand on 2008-09-03
You shouldn't really worry about breakage unless you use -proposed or are on intrepid because most packages are tested pretty thoroughly. In update manager, you can always untick the ones you don't want but it will keep nagging you until you update so the best thing to do is just remove programs you don't want through synaptic (System > Administration > Synaptic Package Manager) click on the "Mark all upgrades" button, then the changes tab and deselect the one's you don't want to upgrade. You can also remove the packages that you don't need from there however you should be sure that you don't need that package.

---

### Post by viaciofano on 2008-09-03
thanks for your help and advice
Vinny

---

