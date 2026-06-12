---
title: "getting nVidia drivers in Jaunty Jackalope"
date: 2009-08-30
forum: Hardware
---

### Post by beezum88@gmail.com on 2009-08-30
I've found a page that describes the process for versions up to Hardy.  Will these instructions work for Jaunty?

Page: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I had it set up when I had SUSE 9 on my computer, but now I've switched to Ubuntu, and I've got to install them over again.

Thanks

---

### Post by hansdown on 2009-08-30
Hi [email]beezum88@gmail.com[/email].

It gets easier in jaunty.

Click system> administration> hardware drivers.

The rest should be very user friendly.

---

### Post by tgeer43 on 2009-08-30
Unless there's something that you've omitted, you ought to be able to just go to System->Administration->Hardware Drivers and install from there quickly and easily.

tgeer

---

### Post by beezum88@gmail.com on 2009-08-30
When I go to Hardware Drivers, it searches for available drivers and comes up with nothing; the window just says "No proprietary drivers are in use on this system" and there's nothing more I can do with it.

I typed in the terminal command in the how-to page I mentioned before (lspci | grep -i nvidia), and got the following:

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

I assume that's the card I have.  After a bit more poking around, I found a forum thread ([http://ubuntuforums.org/showthread.php?p=7643944](http://ubuntuforums.org/showthread.php?p=7643944)) that suggests there are no drivers for my card anymore.  However, I dont' seem to be having the same problems: my monitor runs at native resolution of 1600x1200. Maybe I'll just have to live with no 3D acceleration.

---

### Post by tgeer43 on 2009-08-30
I think you may be in luck. Apparently the Nvidia version 71 driver fully supports the RIVA TNT2 card and is still available in the repositories.

Start the Synaptic Package manager and do a search for 'nvidia-71'. Select the following 3 packages for installation:

nvidia-glx-71
nvidia-71-modaliases
nvidia-71-kernel-source

Hopefully all you'll have to do now is reboot. If the driver is still not functional, go back to Hardware Drivers to see if it is listed and make sure it's selected and activated.

tgeer

---

