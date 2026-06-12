---
title: "Openoffice.org-emailmerge trouble"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by g-raf on 2009-10-04
I've never been able to install/upgrade the openoffice.org-emailmerge package. It seems like a dkms related problem. I can't install any of the new openoffice packages/upgrades in the update manager because of the emailmerge package problem. 

I've tried to remove the package through synaptic, but i get > E: openoffice.org-emailmerge: Package is in a very bad inconsistent state - you should
I should what? That's what i'd really like to know. I can't reinstall emailmerge through synaptic because i've downloaded the updates and it won't let me select reinstall.

---

### Post by g-raf on 2009-10-04
According to what dkms said in the terminal, I need to reinstall the package because it's in a very inconsistent state. How can should i do it?

---

### Post by g-raf on 2009-10-04
I just tried > sudo dkms --configure-a in the terminal, and then > sudo apt-get --reinstall openoffice.org-emailmerge but it went straight back to the emailmerge update and froze immediately.

---

### Post by g-raf on 2009-10-06
I just tried installing the generic kernel and i think it installed.  After installing, it jumped right back into the emailmerge update and  froze. I then manually shut down my compter, restarted it and tried to  load the generic kernel, but there was no generic kernel to  select...only the rt kernel. This is pretty frustrating and i'm hoping  to find a way out of this trouble.

---

### Post by g-raf on 2009-10-06
Please tell me: how can i install and boot the generic kernel? I've installed the generic kernel, kernel image and restricted modules, but there is no generic kernel to select from the kernel screen when restarting the computer. Right now i only have the ubuntu studio rt kernel. I'm hoping that loading the generic kernel will allow me to upgrade/install packages that i need, including security upgrades.

---

