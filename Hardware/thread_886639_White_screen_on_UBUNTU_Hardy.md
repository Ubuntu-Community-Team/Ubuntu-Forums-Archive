---
title: "White screen on UBUNTU Hardy"
date: 2008-08-11
forum: Hardware
---

### Post by cavallipurosangue on 2008-08-11
Hi, all.

booting from live cd AMD64 to try this release, I found, after loading (orange bar), a completely white screen... Any idea? I could not even proceed anyway...

My GPU is an ATI FireGL v8600... Please help me :D

---

### Post by Joeb454 on 2008-08-11
Have you tried booting it in safe graphics mode? I think it's one of the options after pressing F4

---

### Post by cavallipurosangue on 2008-08-11
No, I haven't, but what will I try if I can't login with normal graphics?

Anyway, gutsy is currently installed on, but without proprietary drivers...

P.S.: I can't see any option like that after pressing F4 , ony normal or driver cd or something like that...

---

### Post by jukrsa on 2008-08-11
Hello. I had/have the same problem.
I don't know exactly what is the reason, but try these:
-Use ATI's own driver (admin/hardware menu dialog included one)
-Use lower resolution (I had to go from 1280x1024 to 1024x768)
-Use recovery boots xfix option, and continue
-Edit .gnome2/monitors.xml for all the resolution entries

I did all at some point.

There is something wrong in any case. Ubuntu actually
*broke* my monitor. I succeeded with another old used monitor.

With the first old monitor, before it got broken, the mode
1280x1024 with free drivers for ATI X800 pro worked, but
occasionally had problems. Then I tested various games
and graphics editors with more problems: white squares leaking
over Blender and K3D from Gnome applets. Then with mm3d editor
the monitor got broken.

The new old monitor shows the H sync rate. With 1280x1024
mode it displays 75 kHz even the monitor works only up to
65 kHz. (WinXP runs 1280x1024 / 64 kHz.)

After setting 1024x768, only the Ubuntu logo + progress
bar at the boot and the login display runs in 1280x1024 /
75 kHz mode. How to set them to 1024x768 mode?
I tried limit the HorizSync in xorg.conf but the Ubuntu
only freezed at the boot.

How to set 1280x1024 / 64 kHz mode just as in WinXP?

After switching to ATI's driver, Ubuntu tried 1600x
something mode. Why to pick up the largest screen
if Ubuntu has no idea about the supported H sync rates
of the monitor?

In any case, I have one broken monitor here!

---

### Post by jukrsa on 2008-08-11
> **jukrsa said:**
> 
-Use lower resolution (I had to go from 1280x1024 to 1024x768)


Forum displays a smiley in above. It should be:
I had to go from 1280x1024 to 1024 x 768

---

