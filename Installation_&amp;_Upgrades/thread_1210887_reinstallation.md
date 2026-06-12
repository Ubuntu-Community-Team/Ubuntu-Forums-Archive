---
title: "reinstallation"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by penguinee on 2009-07-12
Hey, 
I installed Ubuntu a while back (w/ Wubi).
I recently wanted to try out Kubuntu, to I proceeded to uninstall. The uninstallation seemed to go okay.
However, after I uninstalled, Ubuntu still remains on the Dual-boot menu. 

Can I delete this in any way?
Or can I just proceed to install Kubuntu since I technically erased Ubuntu? (or maybe I didn't? :confused:)
--
So, to sum it up, is it okay:
to reinstall Kubuntu, even though I can see Ubuntu on my Boot menu?


Thanks!!

---

### Post by unlimitedz on 2009-07-12
I've noticed with Ubuntu (Wubi) that the un-install does not remove the Ubuntu boot entry from "C:\boot.ini".  It i safe to manually remove this entry, just make sure you don't remove the Windows boot string, just the Ubuntu one.

:)

---

### Post by earthpigg on 2009-07-12
> **penguinee said:**
> 
I recently wanted to try out Kubuntu, to I proceeded to uninstall.

in the future, you can simply do this to install kubuntu.... or xubuntu, or edubuntu, or any/all of them:

```
sudo apt-get install kubuntu-desktop
```

then log out. one of the options on the log in screen will be 'select session'. select 'kubuntu', and log into your shiny new kubuntu desktop.

---

### Post by presence1960 on 2009-07-12
> **earthpigg said:**
> in the future, you can simply do this to install kubuntu.... or xubuntu, or edubuntu, or any/all of them:

```
sudo apt-get install kubuntu-desktop
```

then log out. one of the options on the log in screen will be 'select session'. select 'kubuntu', and log into your shiny new kubuntu desktop.

that won't work in this case the OP installed with wubi- the problem is after he removed the wubi install his windows boot still has a menu option for Ubuntu. the solution is to edit the boot.ini file.

---

### Post by penguinee on 2009-07-12
thanks for the replies.
I just have a small problem. 
I can see all hidden folders, but I can't locate C:\boot.ini.


Will look again.

Thanks!!

---

### Post by presence1960 on 2009-07-12
in XP go Control Panel > System> Advanced Tab. Somewhere in the advanced tab is an edit button. That button brings up boot.ini. I no longer have XP so I can't remember exactly but it is in that spot somewhere. When it comes up be careful to only remove the wubi reference.

P.S. I am fixing a couple client's machines and am reinstalling XP. here is the exact location: Control Panel > System > Advanced tab > Start up & Recovery > Settings button > Edit button. This will bring up boot.ini in notepad.

---

