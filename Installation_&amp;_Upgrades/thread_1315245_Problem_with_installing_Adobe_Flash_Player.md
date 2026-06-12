---
title: "Problem with installing Adobe Flash Player"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by wasi_deer on 2009-11-05
I am trying to install Adobe Flash Player Pluggins for my Firefox browser but the followinng error is occured,
**The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.**

---

### Post by pennystockpicksexpert on 2009-11-05
yes!! me to got the same problem with flash player..

---

### Post by wasi_deer on 2009-11-05
I got the solution, which comprises of four steps,
Step 1: Open Application>Accessories>Terminal and then paste this command over there,

Code:
**sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file**

Step 2:
After above command did it task, paste the following in Terminal

Code:
[B]sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
[/B] 
Step 3:
After that,

Code:
**sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin**

Step 4:
and finally, this one

Code:
**sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way**

Try this, I am sure it will work

---

### Post by haidaguy on 2009-11-05
It worked!!
Thank you so much!

---

### Post by dhavalbbhatt on 2009-11-05
Can you please mark as solved?

---

