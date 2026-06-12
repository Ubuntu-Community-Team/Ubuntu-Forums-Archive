---
title: "Nvidia driver issues"
date: 2009-08-08
forum: Hardware
---

### Post by carsten- on 2009-08-08
Hello people!
I'm having an issue with Binary nvidia drivers for Jaunty.. I have searched the forums, for the same error found some results but none of which have fixed my problem.

This is the error I get:

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Allow me to document my efforts thus far:
Made sure correct Kernel headers are installed
Made sure I am using the 180 drivers as available in the restricted repository
Unloaded and reloaded the kernel module "nvidia" manually
Tried shutting down gdm, doing a remove and reinstall of the drivers
Tried putting the system in run level 3 to remove and reinstall the drivers
Tried older drivers
Made sure all kernel common modules are installed etc.

I was using a nvidia 7300LE, thinking that might be a tad old or not working correctly I have been out to purchase a new Nvidia 9400GT, have clean installed the system and still have the exact same issue.
I have checked all available forums for this issue, is anyone able to help?

---

### Post by kdi on 2009-08-08
hi...
I think i have the same probs with my nvidia geforce fx5500. "no screens found".

but i managed to solve all issues.

i believe the problem is with the modules n xorg.conf files. you have to configure them by urself as the driver doesn't able to do it automatically for you. its quite confusing at a moment but believe me, after its been setup correctly, u can sit n playaround with all 3D effects of compiz n having fun with video games on your system.

i have made a howto video on how to install the driver. i prefer to download the driver from nvidia.com n install it manually. logon to my blog n watch the video. hope it will help you...=)

[http://paktamcyber.blogspot.com/2009/06/its-nearly-week-for-me-to-configure-my.html](http://paktamcyber.blogspot.com/2009/06/its-nearly-week-for-me-to-configure-my.html)

---

### Post by carsten- on 2009-08-08
Thanks for the info, but I have already tried this to no avail. I did try one more time, still no luck.


> **kdi said:**
> hi...
I think i have the same probs with my nvidia geforce fx5500. "no screens found".

but i managed to solve all issues.

i believe the problem is with the modules n xorg.conf files. you have to configure them by urself as the driver doesn't able to do it automatically for you. its quite confusing at a moment but believe me, after its been setup correctly, u can sit n playaround with all 3D effects of compiz n having fun with video games on your system.

i have made a howto video on how to install the driver. i prefer to download the driver from nvidia.com n install it manually. logon to my blog n watch the video. hope it will help you...=)

[http://paktamcyber.blogspot.com/2009/06/its-nearly-week-for-me-to-configure-my.html](http://paktamcyber.blogspot.com/2009/06/its-nearly-week-for-me-to-configure-my.html)

---

### Post by kdi on 2009-08-08
what monitor n processor are u using?

does ur mobo have the integrated graphic accelerator?

could u post ur xorg.conf?

---

