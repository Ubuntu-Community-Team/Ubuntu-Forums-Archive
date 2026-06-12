---
title: "Suspend black screen - Dell Inspiron 8500 (Nvidia 4200 Go), nvidia96 driver, 12.04"
date: 2014-01-18
forum: Hardware
---

### Post by wb0gaz on 2014-01-18
Need to get recover from suspend working on a Dell Inspiron 8500 running Ubuntu 12.04 and the Nvidia 96 driver (restricted driver offered when system first installed.) Nouveau does not work properly for this machine (significant visual artifacts.)

While running nvidia-96 (I did not test suspend/recover with Nouveau), when coming out of suspend (via system menu), screen is black, backlight is operating, no cursor. When in this state, I can access the machine via ssh server so it is running. Accessed from ssh, top says Xorg is running nearly 100% CPU. I can reboot it this way, although it takes a long time (minutes) to complete the reboot (due to CPU load I suspect.)

I tried pm-suspend (via command line) and got same result.

I connected to the VGA port on back of laptop, no signal.

From what I can tell, this is a legacy driver per Nvidia website, so the 96xx driver appears to be the correct one to use:

ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/README/appendix-a.html

"Below are the legacy GPUs that are no longer supported in the unified driver. These GPUs will continue to be maintained through the special legacy NVIDIA GPU driver releases.

The 1.0-96xx driver supports the following set of GPUs:
NVIDIA chip name 	Device PCI ID
...
GeForce4 4200 Go 	0x0286"

Thanks for any advice, or pointer to where I should seek assistance!

Dave

---

