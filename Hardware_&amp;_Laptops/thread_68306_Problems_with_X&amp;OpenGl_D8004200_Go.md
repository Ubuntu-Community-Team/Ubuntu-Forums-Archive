---
title: "Problems with X&amp;OpenGl D800/4200 Go"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by hangfire on 2005-09-22
Hi all,

I have a custom OpenGL app I need to get running on a Dell D800 running Kubuntu 5.0.4 with the latest updates. It runs fine on a similarly configured K5.0.4 desktop machine with an nVidia MX400 running "nv" in /etc/X11/xorg.

When I first ran it with xorg.conf set to "nv" on the laptop it complained about missing support (OpenGl or glx or something I forget) so I installed the official nvidia packages (1.0.7174) and edited the xorg.conf to "nvidia" (and the load edits like dri) which fixed that problem. glxgears runs fine at 2700fps. However when I run the app it gets a segmentation violation in glXChannelRectSyncSGIX () from /usr/lib/libGL.so.1. Apparently this is a known bug and the fix is to update the drivers.

I tried 1.0.7676 and X bombed out on launch.  So I tried 1.0-7667 but I got a blank screen on the external 1600x1200 monitor.  I have to Ctrl-Alt-Bksp to get out. Then I started hacking. I put something about nvidia_laptop equal to 0 or 2 at the bottom of /etc/modprobe.d/nvidia-kernel-nkc (I forget the exact syntax). Everything ended in either Ctrl-Alt-Bksp or Ctrl-Alt-Dlt.

One problem I've had getting help is, "glXChannelRectSyncSGIX" is too long a term to search for on vBulletin. :(

Any ideas?

HF

---

### Post by hangfire on 2005-09-23
I have temporarily "solved" the problem by uninstalling all nvidia drivers, going back to "nv" in xorg.conf, and then reinstalling xorg-server, which restored the libglx.a file in extensions that I deleted as part of one of the many howto's.

glxgears and my custom app now run, very slowly, but they run, which is what matters most.

Apparently this is a known bug and nvidia has done nothing about it for about 3 years now. Sad.

---

