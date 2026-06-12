---
title: "Graphics card shuts down when laptop switches to battery"
date: 2011-03-31
forum: Hardware
---

### Post by wheremyhatisat on 2011-03-31
I just installed Ubuntu 10.10, and I'm new to this, so bear with me.
Everything works fine until I switch my laptop over to battery power. At that point, the screen dies completely. If I plug it back in, half of the screen comes back, but it's still very dim. It also says that my battery is critically low, even if it's at 100%.
I've tried changing quiet and splash to xforcevesa in GRUB, as well as changing it to nomodeset. nomodeset keeps the screen alive when I unplug the computer, but only for 30 seconds or so, and then it dies. 
My GPU is an nVidia 330m. Installing the official nVidia driver makes it so that I can't boot up at all, I just get a blank screen. Any help would be great. When my laptop is plugged in, everything works great, and I love ubuntu, but it's not a laptop if I can't ever unplug it.

---

### Post by papibe on 2011-03-31
It sounds like you have [Optimus]("http://www.nvidia.com/object/optimus_technology.html"), which is not yet supported in Linux.

I believe some laptops, not all, have a feature in the BIOS to disable it. Which is the exact brand and model of your machine?

Regards.

---

### Post by wheremyhatisat on 2011-04-01
It's a vaio VPCF1, I'll check the BIOS, that's likely the problem, thanks!

---

