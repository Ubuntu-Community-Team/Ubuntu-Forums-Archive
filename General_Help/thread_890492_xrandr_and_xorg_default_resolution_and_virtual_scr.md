---
title: "xrandr and xorg default resolution and virtual screen size"
date: 2008-08-15
forum: General Help
---

### Post by jbebel on 2008-08-15
Hello.  I'd like to find a way to have a default screen resolution for GDM and new users that is smaller than the maximum allowed resolution accessible by xrandr, and I can't seem to find a way to do it.  Here's what I've done:

I installed ubuntu hardy, and my CRT, which looks best at 1024x768 wound up displaying at 1600x1200.  I can change my resolution using xrandr (gnome monitor resolution settings), but that doesn't affect GDM, or other new users on the system.

I tried setting the mode to 1024x768 in /etc/X11/xorg.conf, but that leaves xrandr with nothing bigger than 1024x768.  I'd really like a user to be able to select a higher resolution if they choose, but still default to 1024x768.

So I tried various methods of adding higher modes, or adding a virtual line with higher resolution, but these all result in having a larger virtual screen size with only 1024x768 visible.  The gdm login box winds up off-centered, or if the virtual screen size is too big, it winds up off-screen.

I see several guides, like thinkwiki and on debian.org that give large values for virtual.  Based on my experience, I don't see how that isn't making the gdm login box off-center, or completely off-screen like I'm seeing.

So, how does one make the default and GDM resolution something pleasant and accurate, while still allowing xrandr applications to increase the resolution if desired?

---

### Post by DouglasAWh on 2008-08-21
I'd like to know how to do this too...

---

