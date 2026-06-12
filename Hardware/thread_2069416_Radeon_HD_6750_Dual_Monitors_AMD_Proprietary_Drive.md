---
title: "Radeon HD 6750 Dual Monitors AMD Proprietary Driver Issue"
date: 2012-10-10
forum: Hardware
---

### Post by kronflux on 2012-10-10
Hey!

So I've got two monitors, one supports up to 1920 and the other supports up to 1280
I installed the AMD Proprietary driver from their website, and opened Catalyst in administrative mode.

I was able to set up the desktop to extend across both screens, and was able to set the resolutions for each monitor without issues.
Upon applying the settings, I did encounter an issue where the catalyst window was off the screen during the "are you sure you want to keep these settings" bit, but by applying again with the window moved to the edge of the screen, I was able to click yes, and everything worked great.

So that's that. It works great. Until I reboot.
Upon rebooting/logging off, the settings go back to defaults. The displays are mirrored again, and the monitors are at the wrong resolutions.

The settings worked fine with the default drivers, but I do intend to do some gaming and some graphics editing on this machine, so I do want the best support possible for my hardware.
And again, these drivers work great! The only issue being the settings reverting back to defaults..

So is there a way to.. "lock" these settings? or uh. load them on bootup? or something?

Thanks in advance!

---

### Post by m1tche11j on 2012-10-11
I had the same issue, and the only way I could fix it was was to set the display resolution in CCC after the resolution was set, goto regular "Displays" control panel and set them there to and click apply. 

Then after reboot it finally stuck.

---

### Post by tajmox on 2012-11-06
> **m1tche11j said:**
> I had the same issue, and the only way I could fix it was was to set the display resolution in CCC after the resolution was set, goto regular "Displays" control panel and set them there to and click apply.

Thanks, this was bugging me. Now it's the correct resolution even after logout.

---

