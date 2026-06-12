---
title: "HDMI audio/video woes with Nvidia 5200m"
date: 2019-03-02
forum: Hardware
---

### Post by dennis1200 on 2019-03-02
I have a Dell latitude e6530 with integrated Intel graphics and a discrete 1gb nvs 5200m graphics card. It seems like the HDMI connector is part of the Nvidia card. I have had extremely variable results with hdmi, but usually it doesn't work at all with an external monitor. The frustrating part is that I did get it all to work, once, video and audio, and auto detect of a second screen, but on restart it went back to not working.&#128574;

I'm running Ubuntu 18.04 on the latest kennel and using the Nvidia 390 driver. I have tried the driver from the repository and the graphics drivers PPA, same results (they're the same version). The only time I got it to work flawlessly was by installing the nouveau driver, purging all of the Nvidia packages, disabling Optimus in my BIOS, then reinstalling the Nvidia packages. However, after waking from suspend or restarting the computer, it hangs on boot, seemingly at an unrelated step in the process, usually but not always something about snapd (probably unrelated). I can't get to the login screen, and the only way I can is by enabling Optimus in the bios, which always means that the HDMI output does not work at all. I cannot detect the second monitor in multiple display managers, or using the Nvidia settings to detect displays. The HDMI output does not work using the nouveau driver, and overall video responsiveness is noticeably worse. I'm basically at the point where my next step is to try using a VGA to HDMI adapter, but it would be really nice to have a functional HDMI port. Any help is very appreciated and I know this is something of an issue. But seemingly unresolved based on all the web searches I've been doing. More common is video but no audio, which I actually had for a while until that stopped working after a few kernel updates.

---

### Post by dennis1200 on 2019-03-03
SOLVED: After looking at the various bug reports with nvidia 390 drivers, I realized for sure that Optimus needed to be disabled for it to work but it would hang on boot. I also saw a lot of bug reports with the way gdm3 treated nvidia hardware. I got things working by running dpkg-reconfigure to switch my display manager from gdm3 to lightdm. It's obviously not a perfect solution, but it seems like the hangup was just getting to the login screen. I can still log into standard Ubuntu using Gnome 3 and have fully functional audio and video on HDMI, but the login screen needs to be in lightdm. Hopefully this helps some folks because I've seen a lot of similar reports on other forums, and nobody really hit on the lightdm solution.

---

### Post by CatKiller on 2019-03-03
> **dennis1200 said:**
> I got things working by running dpkg-reconfigure to switch my display manager from gdm3 to lightdm. It's obviously not a perfect solution, but it seems like the hangup was just getting to the login screen. I can still log into standard Ubuntu using Gnome 3 and have fully functional audio and video on HDMI, but the login screen needs to be in lightdm.

In case you were curious as to why that works, GDM decides that if you have accelerated 3D graphics at all then you must use Wayland... which doesn't work with Nvidia. It's not a good decision, and it's a particularly bad decision for a Long-Term Support release.

---

### Post by dennis1200 on 2019-03-05
> **CatKiller said:**
> In case you were curious as to why that works, GDM decides that if you have accelerated 3D graphics at all then you must use Wayland... which doesn't work with Nvidia. It's not a good decision, and it's a particularly bad decision for a Long-Term Support release.

I do vaguely remember seeing something like that in the bug reports. That's just so silly!

---

