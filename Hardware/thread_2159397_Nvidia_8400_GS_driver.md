---
title: "Nvidia 8400 GS driver"
date: 2013-07-03
forum: Hardware
---

### Post by howcanireachthesekids on 2013-07-03
Hello!
I am going crazy here, been all over this problem for about 12 good hours now, yet no solution. Here are my specs.
Monitor : ASUS P203W
Card : Nvidia 8400 GS

The only way for me to boot Ubuntu, Kubuntu, Xubuntu 13.04  is through "nomodeset". If I dont boot via that, the monitor will go into sleep mode and say "No signal"
Now, when I boot and login, the maximum monitor size I can select is 1024 x 768, using nouveau driver. I want to know, why and how to solve it? What driver do I need for my graphic card that works fine? Is it a driver problem at all?
How do I get my monitor to show 1680x1050 monitor resolution as it should? I am going crazy :(

Thanks in advance to anyone who would be willing to help, I will be monitoring this thread.

EDIT : I installed the latest Nvidia drivers as it says here [http://ubuntuforums.org/showthread.php?t=1771806](http://ubuntuforums.org/showthread.php?t=1771806), rebooted, launched nvidia-settings, but still could not select my monitor's real resolution. It added a few new resolutions however.
Please someone just help me!

---

### Post by dino99 on 2013-07-03
in case of xorg.conf, then delete it as the kernel now directly deal with X:
> sudo rm /etc/X11/xorg.conf*

that card needs nvidia-173 (or nouveau), so purge everything else, and install (reinstall) that one.

---

### Post by kurt18947 on 2013-07-03
I have an Nvidia 8400GS & seveal years old Westinghouse monitor.  I had some power management issues when using the nouveau driver but only when resuming after suspend.  I've never had a problem after a reboot.  The Nvidia drivers have always worked though 304 wasn't flawless.  I typically use the Nvidia current (not experimental) driver with no issues.  Here is an Nvidia doc that addresses which drivers support which cards:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

It looks like the 319.32 driver should work for you, it does for me.  I don't download from Nvidia but install via the latest iteration of 'addititional drivers'.

---

### Post by deadflowr on 2013-07-03
> **dino99 said:**
> in case of xorg.conf, then delete it as the kernel now directly deal with X:


that card needs nvidia-173 (or nouveau), so purge everything else, and install (reinstall) that one.

No it doesn't. It'll run fine up to the latest, which now is 319.XX.

Added: What other settings does it let you pick?
Unfortunately, there might be a good chance that the EDID for the monitor is unreadable by the linux drivers.

---

