---
title: "[SOLVED] Automatic Switching to External Monitor on Laptop?"
date: 2008-09-29
forum: Hardware
---

### Post by SamNSane on 2008-09-29
This is a video subsystem configuration issue, but it's peculiar to laptops.

I've got a laptop that I use with its built-in display (1920x1200) when away from my desk. When I come back to the desk, I dock the laptop with the lid closed and use a 1680x1050 external display (DVI).

When using the Open Source drivers the system is smart enough to know that I want to use the external display when I'm docked with the lid closed. It automatically adjusts the screen resolution between the two modes of use, too.

BUT...

When I install the restricted (nVidia) driver from the repository the system becomes stupid. At boot time when docked I see the POST and most of the boot process on the external monitor, then the screen becomes blank, and I hear the login prompt sound. The login window is being displayed on the built-in display. I have to open the lid, hit Fn-F8 to throw video to the external display. And even though I have set the built-in display to use 1680x1050 just like the external display (because with the restricted drivers the system doesn't deal well with switching back-and-forth) the doggoned login window comes up at 1920x1200.

QUESTIONS:
1. Is this happening because the restricted drivers themselves have a problem, or because something bad happens to xorg.conf when the restricted drivers are installed?
2. The important question is -- is there any way for me to fix this?

BTW, I have already tried nvidia-settings. Insofar as I can tell, there's absolutely nothing that applet can do for me. If I were going to use both monitors simultaneously I might be interested. But I find dual monitor support under the Linux distros I've tried to be dismal compared to multi-monitor support in XP/Vista. But I've switched all my systems to Ubuntu because -- except for the video issue and a minor problem with burning optical discs to a USB-connected DVD-RW drive -- I like the OS a lot more.

If someone can tell me how to fix this silly little issue I'll be very grateful.

Thanks,
Sam

---

### Post by SamNSane on 2008-10-01
Here's to the developers who do the Open Source drivers. Big thumbs up. I'm sorry I won't have 3D or desktop effects even though I'm using a video subsystem with 512 MB of dedicated memory, but I'd rather have solid basic functionality, and that's what the Open Source drivers provide.

And thumbs down and a big razz to nVidia. Yeah, you write drivers for Linux. Maybe if you'd open the source the Linux guys could show you how to write drivers that actually handle basic functionality with a little flexibility. Instead, you make your customers who use Linux pound sand.

I paid several hundred extra to buy the nVidia CAD-capable OpenGL video subsystem on this laptop, and it doesn't work worth spit under Ubuntu. Not only can I not have 3D, I can't have any special desktop effects at all on this expensive system. You guys won't be getting any money from me again.

I've also got a dinky little Panasonic sub-notebook with an integrated Intel video subsystem. Of course 3D is a little lame on it, but I've got all of the best of the desktop effects with an Open Source driver.

Thumbs up to Intel -- and again to the Open Source driver guys. In Ubuntu this little thing screams, and it's got better desktop graphics than it had under Vista, including terrific transparency support.

Which I DON'T have on the expensive Dell Precision notebook with the expensive nVidia video card.

---

### Post by shan63amg on 2008-10-01
hey man i feel your payne.... i also have the exact same problem with my dell d800 laptop and docking station. i've noticed all the things that you have too. as far as i can seee there's no way to fix it except for complaining to nvidia:(

---

### Post by SamNSane on 2008-10-01
> **shan63amg said:**
> hey man i feel your payne.... i also have the exact same problem with my dell d800 laptop and docking station. i've noticed all the things that you have too. as far as i can seee there's no way to fix it except for complaining to nvidia:(

I complained to nVidia support and at nvnews. I didn't receive a single response. They've decided upon their business model, and they're not budging.

I've decided on my business model, too. They ain't gettin' any more from me.

---

