---
title: "Olidata U40SL1 notebook - won't complete boot on battery power"
date: 2017-01-28
forum: Hardware
---

### Post by lah-ca on 2017-01-28
[SIZE=4]**Preamble**[/SIZE]


I am refurbing an older Olidata U40SL1 notebook for charity. This notebook is apparently identical to ECS, Uniwill, and Olivetti units with the same model number. 


I am stress testing the notebook, trying to get it to a point where a non-techie user could be happy with it. 


(See back story and successful efforts with SIS video drivers here: [https://ubuntuforums.org/showthread.php?t=2350126](https://ubuntuforums.org/showthread.php?t=2350126) and peculiar transient self-resolving problem/non-problem with wireless NIC here: [https://ubuntuforums.org/showthread.php?t=2350792](https://ubuntuforums.org/showthread.php?t=2350792) )


[SIZE=4]**OS**[/SIZE]


The notebook is loaded with LUbuntu 16.04 32 bit.


[SIZE=4]**Problem**[/SIZE]


The notebook will not boot fully when powered by battery.  


The battery is in remarkably good condition for unit of this age: doing nothing in particular, the notebook will run for over an hour on a fully charged battery; netsurfing and watching Youtube videos, it will run for 35 minutes plus.


With the battery fully charged and with the notebook disconnected from the power adapter, attempts to boot end up with the notebook going into some sort of suspend mode.  POST/boot goes normally to the LUbuntu splash screen where the dots go across the screen; then the screen goes black as it normally does, but instead of continuing to load the OS, everything stops, and the power-on indicator light starts blinking as it does if the notebook is suspended.

I do not recall it doing this with Vista Starter, but I may not have tested booting on battery power.

Ideas?

---

### Post by lah-ca on 2017-01-29
Curiously, if I boot up with the power adapter attached, unplug the power adapter, and then hot reboot, the notebook will complete the boot process successfully with only battery power. 

If I immediately then shut it down and cold boot without the power adapter, it will never complete booting but will go to a suspended state.

---

### Post by lah-ca on 2017-01-30
After using Google translate to troll through Spanish language support forums and following up dead links at Wims BIOS, I see that this particular model of laptop has been plagued by BIOS problems - battery won't charge, can't install 2 Gb SODIMMs, can't use DDR2 800, wireless NIC issues, etc.  I suspect that the inability to cold boot from battery is just one more BIOS problem.  And I am probably 5 years too late to find an updated BIOS anywhere.  And it appears that all the people who sold this notebook would just like to see it vanish from the face of the earth.

---

