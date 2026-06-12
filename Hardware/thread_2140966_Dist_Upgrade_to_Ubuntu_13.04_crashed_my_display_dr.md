---
title: "Dist Upgrade to Ubuntu 13.04 crashed my display drivers"
date: 2013-05-01
forum: Hardware
---

### Post by Alan_D. on 2013-05-01
Hello everyone,

I was using UbuntuStudio 12.10 with the official Nvidia drivers (graphics card: GTX550 phantom), a 2-monitor setup with XFCE 4 as desktop manager and everything was working very nicely. Now I've done a dist upgrade to 13.04 and while everything else works, the Nvidia drivers don't for a reason unknown to me. My display is down to a resolution of 640x480 (yuck!) and my second monitor isn't even recognized by the system.
Now, I do not neccessarily need to use the nvidia drivers, because I don't play games under Linux (yet), so I'd be happy with any generic display driver that supports two monitors and can get the resolution back up to 1920x1080. Unfortunately I've got absolutely *no clue *how to do this. 

Any help would be apreciated!

Thanks,


Alan

---

### Post by grahammechanical on 2013-05-01
So, you can get to a working desktop? You can select About this Computer or System Settings from the power/cog menu (it might be a bit different on Ubuntu studio - I am not using it) But once you open System Settings go to Software & Updates and open the Additional Drivers tab and re-activate the video driver. There should a list that you can experiment with. Nouveau is the open source driver.

It seems that upgrades often break video drivers because we get newer Linux kernels that need newer video drivers and from my experience some proprietary video drivers are not as safe as they once were.

Regards.

---

### Post by Alan_D. on 2013-05-01
Hi,
thanks for your answer. Yes, I can get to a fully working desktop, only restricted to 640x480 resolution. I've found the window you were talking about and set the driver to the open source driver Nouveau. Afterwards I restarted my PC, which unfortunately does not solve my problem. In the System Settings -> Display menu, I cannot set the resolution to anything higher than 640x480 (xrandr tells me the same). Also, I cannot switch back to the Nvidia driver in the drivers menu - every time I try and click apply, the selection will just jump back to Nouveau without any comment.

Any ideas? I'm afraid that I'll have to re-install my linux if this continues on like that... (and that's definitly NOT something that I'd like to do)

Thanks,


Alan

---

