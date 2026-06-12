---
title: "Unable to load nvidia drivers after kernal/software update"
date: 2008-11-29
forum: General Help
---

### Post by Tomdarkness on 2008-11-29
Hey,

Last night I ran software update and it updated the kernel. Now when I booted this morning it wanted me to start in low graphics mode with this error:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

If I go into System -> Administration -> Hardware Drivers it says "No proprietary drivers are in use on this system" and I have a option of two NVidia drivers (version 173 and 177). If I try and activate the recommended version 177 it comes up with the normal "Downloading and installing driver" but never activates.

Edit: Also unable to activate the version 173 driver.

Update: Reinstalling the NVidia drivers that I downloaded from the nvidia website has appeared to fixed the problem - do I have to do this after every kernal update, seems a bit tedious?

What is up? I need graphics acceleration ASAP.

Thanks,

Tom

---

### Post by PmDematagoda on 2008-11-29
The problem is probably due to the Nvidia driver package from the repos not having being synced with the current kernel version on time. Perhaps if you had been a bit patient and then rechecked with Hardware Drivers, it may have installed.

And yes, you do need to reinstall the driver manually with every kernel update, which is something usual with most proprietary drivers. However, if you manage to get the Nvidia driver working with the Nvidia driver from the repositories, then you do not need to do that yourselves.

---

### Post by Tomdarkness on 2008-11-29
Thanks for the info - ill just live with reinstalling the drivers then. Only takes a few minutes. The only reason I am useing the none-repository driver is that I find I get better performance out of it.

---

### Post by old-n-gray on 2008-12-05
I am new at this, have just installed Hardy.  I am trying to find out how to install Nvidia drivers for my 9800GTX. Any suggestions, perhaps advise me how you installed yours.
Thanks

---

### Post by borlosky on 2009-01-14
i had same issue after kernal update, surprisingly all i did to get it working, is i installed the new 177 driver, but i got errors (low graphics mode as well upon reboot), so i removed driver then rebooted. then tried to install 173 drivers got errors as well, didn't get low graphics mode, but i also couldn't enable compiz. so now i removed 173 drivers, rebooted again, then went again for 177 drivers, got no errors this time, rebooted, all is working fine ever since. 

the only other problem i noticed with the update, is it completely unchecked EVERY compiz-fusion plugin, and removed all my key bindings for said plugins. (good thing i made a back up of my compiz settings, so that was an easy fix at least)

---

