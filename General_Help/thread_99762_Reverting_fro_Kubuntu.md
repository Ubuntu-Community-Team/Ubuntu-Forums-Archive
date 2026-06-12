---
title: "Reverting fro Kubuntu"
date: 2005-12-06
forum: General Help
---

### Post by cougem on 2005-12-06
Hi I originally installed ubuntu onto this machine, and got to love Gnome. Then I thought I'd try out KDE. It's nice, but not quite so sleek. How do I fully revert back to gnome, and lose all the kubuntu grpahics etc? I'd like to keep the programs though.

Would it just be sudo apt-get remove kubuntu-desktop? Because that only seems to be removing around 250kb of data!

Many thanks,

-James

---

### Post by tonym on 2005-12-06
unfortunately,  if you install a package with apt-get or synaptic it installs the dependencies,  but won't remove dependencies when you remove the original package.  I use aptitude to install/remove packages because it will remove dependencies automatically.

However,  that doesn't help you now!  The only way I have got round this is to load aptitude and then search for packages with kde in the name.  When you remove the major ones - kdelibs - anything depending on them will become broken.  Use the "b" key to find the broken packages and remove those also until there are no broken ones left.  I have done this and it doesn't take too long.

Regards

Tony.

PS  When I next install Ubuntu/Kubuntu I think I might just do the basic install and then add ubuntu-desktop or kubuntu-desktop via aptitude.

---

### Post by cougem on 2005-12-06
Hi yeh, I just ended up formatting and reinstalling ubuntu then actually. Felt like a fresh install.

Is there a quick way to install the KDE utils/programs without having to install the desktop environment and such? Via apt-get say?

Thanks!

---

### Post by pheitman on 2005-12-06
Go ahead and install kubuntu-desktop (assuming that you have the hard drive space. When you are asked whether to use kdm or gdm as the login manager, choose gdm (the one that comes with gnome). During login you can specifically choose whether to use gnome or kde for that particular session. If you don't choose it will use the default which will likely still be gnome. 

Peter

---

