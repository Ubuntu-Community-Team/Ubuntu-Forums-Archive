---
title: "System restart on certain actions, might be related to gfx drivers"
date: 2013-04-08
forum: Hardware
---

### Post by wmdvanzyl on 2013-04-08
*********** EDIT: running failsafeX returns the following error in the log file:

> (EE) Screens found, but none have a usable configuration.

> Fatal server error: No screens found

Also, i recently switched to a new display. Could this have any influence?

***************************

Hi All.

Recently had a amd gfx card (hd6870) die on me and so it was sent in and thankfully RMA'd. In the meantime i swapped in a different gfx card (some entry level nvidia), but to get it to work i had to reset the bios (had to do with the onboard gfx) and i had to remove the amd drivers and isntall the nvidia drivers. Now i ahve my amd card back in the machine and i have reversed the driver installations. I also messed around in compiz-settings (don't know what prompted me to do this) and that's where i first noticed the problem. On some animations/transitions the system would simply reboot. I promptly disabled those, but the same thing happened in firefox when access flash or video content. Lastly, i can consistently reboot the system by opening Steam and trying to log in. I believe the common factor here is the gfx driver, but i am not sure. 

I have tried installing different variations of driver from synaptic, but the issue remains. I don't see anything being recorded in the log files, but i am not very knowledgeable with those. What can i post here to help you help me resolve this issue?

Thanks!

*** Edit. I have removed compiz-settings just to cover the possibility of it being that, but to no avail. If someone has any advice on where i can start looking at why my system just reboots, i would really appreciate it.

*** Edit. When booting in safe mode and using failsafeX, it gives some error about not detecting the screen, but if i hit ctrl-c at that point it continues (otherwise it aborts and returns to recovery-mode screen), but then also crashes randomly once the desktop is reached.

*** Edit. So i have determined that the problem is that X server is still trying to use the Nvidia drivers from the short period is was using the nvidia card. The last error in all the logs says there is no screen and before that just a whole bunch of calls relating to nvidia. I have tried to stop lightdm from tty and forcing x to reconfigure using x --configure, but it keeps recreating the erroneous conf file. Where is it getting this from? How can i fix it?

---

### Post by wmdvanzyl on 2013-04-09
Anyone?

*** EDIT: found that i had no hardware accelleration either. glxgears gave me 60fps. Downloaded drivers from amd website. Gave me accelleration and crashing has magically stopped. So no amd drivers in the package managers worked for my hd6870 - shocking. 

I can still consistenly crash the system by trying to log into steam, but that might be a completely unrelated issue,

---

### Post by wmdvanzyl on 2013-04-23
Now i'm totally locked out of my system! I opened Chromium and the system rebooted and i have been unable to get back in. It gets to the ubuntu loading screen and then drops me into a prompt. I have tried uninstalling lightdm and installing gdm, but to improvement. It seems X doesn't start, but i'm not sure.

Please.Help.

---

