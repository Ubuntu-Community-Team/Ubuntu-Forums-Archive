---
title: "I've broken my nVidia setup"
date: 2008-04-26
forum: Hardware
---

### Post by peter.marks on 2008-04-26
I was trying to get my Feisty setup to suspend more reliably and have now got into a bit of a mess. I tried various things (detailed below), but I think it was installing the latest nVidia driver (from nVidia) that has caused the problems.

When I boot my machine now it goes into low resolution mode (using xorg.conf.failsafe). I can get it working by logging in to a console, stopping GDM, unloading then reloading the nvidia kernel driver and restarting GDM. However, I get into the same mess on the next boot... oh and now suspend seems to hang on restore every time... and I have some weired flickering when I mouse over title bars which wasn't there before.

What should I do? Let me know what config or log files I should upload to give more information.

History:

I've been running this setup using the proprietary nvidia driver from the repositories since October and has been pretty stable. However, suspend to RAM worked only intermittently: a couple of times it would be fine, then it would suspend and come back immediately. Suspending again produced the same result. The only way I found to get it to suspend correctly again was to reboot. Occasionally, it would suspend fine then not resume correctly: lights would go on and power utilization would go up (my psu has a display), but the display would not initialize. Pressing the power button again would send it into a suspend resume loop which could only be stopped by pulling the plug.

In an effort to resolve this I tried some power related packages from the repositories such as uswsusp. I had no success.

Doing some research suggested I should use the setting "NvAGP" "1" in my xorg.conf and blacklist any agp drivers. I blacklisted "intel_agp" and this seemed to work fine, but didn't improve anything.

Having removed all the power packages I tried and restored packages that I had had to remove, I then decided to upgrade to the latest driver from nvidia. I downloaded and ran NVIDIA-Linux-x86-169.12-pkg1.run. After this my machine has been in the state described above.

I tried reinstalling the nvidia driver from the repository, reverting the kernel (which seemed to have been replaced at some point during my messing about), running the nvidia installer with the uninstall option and re-installing with the nvidia installer. That is where I am at now.

Any help gratefully appreciated.


Peter

---

