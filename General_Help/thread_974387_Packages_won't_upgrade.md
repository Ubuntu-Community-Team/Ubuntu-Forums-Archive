---
title: "Packages won't upgrade"
date: 2008-11-07
forum: General Help
---

### Post by wildman4god on 2008-11-07
Can someone please tell me why there are packages in update manager that refuse to update, it seems that the updates are avalible and they are listed but the check box won't check.

---

### Post by wildman4god on 2008-11-07
Hellooooo

Anybody there?

Echo...echo...

:confused:

---

### Post by cdtech on 2008-11-07
Have you tried the command line:
sudo apt-get update
and what messages do you get?
You could also try the command line:
sudo apt-get autoremove && sudo apt-get autoclean

**From the man page:**
> autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

---

### Post by stoneage on 2008-11-07
I get that too, usually it is because they need to install dependencies.
You should be able to install the updates from synaptic package manager - click on the big 'Status' button then go to 'Upgradable'.
I've no idea what the cause of it is though.

---

### Post by applegrew on 2008-11-07
Packages that need to install new packages as dependancies are considered not-'*safe*' upgrades. You should use the command **sudo apt-get dist-upgrade**

---

### Post by stoneage on 2008-11-08
> **applegrew said:**
> Packages that need to install new packages as dependancies are considered not-'*safe*' upgrades. You should use the command **sudo apt-get dist-upgrade**


Do you mean dist-update ?
Surely if I **sudo apt-get dist-upgrade** I will upgrade to Ibex. (Won't I?)

---

### Post by applegrew on 2008-11-08
There is no such option as dist-update. Though the name sounds like it will upgrade to next distribution, but it actually won't. If you use **aptitude** then the equivalent for *upgrade* in **apt-get** is *safe-upgrade* and equivalent of *dist-upgrade* is *full-upgrade* in **aptitude**.

---

### Post by stoneage on 2008-11-08
OK, thanks.

---

### Post by wildman4god on 2008-11-08
Thanks, that worked, though there are still to packages that won't upgrade, ffmpeg and mplayer, any ideas on these?

---

