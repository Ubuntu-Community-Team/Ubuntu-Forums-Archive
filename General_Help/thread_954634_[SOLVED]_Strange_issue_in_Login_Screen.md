---
title: "[SOLVED] Strange issue in Login Screen"
date: 2008-10-21
forum: General Help
---

### Post by small_sammy on 2008-10-21
Hi to all, this is my first post!

I installed yesterday Xubuntu 8.04 and almost everything is going fine.

I have a 19'' Belinea monitor and NVidia 650gt graphics card. I installed the NVidia drivers and configured the monitor for the exact model I am using, also did setup my screen resolution to 1280x1024.

My desktop appears fine, but there is a problem when booting and the system comes to the login screen. It seems like the resolution is different for the login screen, everything appears out of place( to be more specific it seems like Xubuntu thinks I have a bigger monitor, or maybe 2 monitors installed....the login box appears to the bottom right of the screen, and everything is bigger than expected)

I checked my xorg.config file and the only resolution declared there is 1280x1024.

Any ideas?
Thanks for reading this (hope it is not very confusing)

---

### Post by Sycron on 2008-10-21
Try this. [http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

---

### Post by small_sammy on 2008-10-21
Thank you for your quick reply...

I will re-check my xorg.conf and see how that goes.

---

### Post by Ameneon on 2008-10-23
That was precisely it, Sycron (the comment by Anne further down, did not try the solution offered by the blogger himself). Thanks a lot!

---

### Post by Sycron on 2008-10-24
The comment is almost the  same thing which the blogger said, lol. :)

---

### Post by small_sammy on 2008-10-24
For me worked just by changing the "Virtual" setting.

Thanks!

---

### Post by Ameneon on 2008-10-24
> **Sycron said:**
> The comment is almost the  same thing which the blogger said, lol. :)

Well, the blogger himself mentioned removing all modelines that one did not want to use, whereas the comment I meant said to modify the Virtual setting as well as moving the resolution preferred to the beginning of the main mode line.

In any event, huge thanks again, with any luck I'll get the remaining quirks worked out now again and can proceed with enjoying Ubuntu like I did when I first started using it :)

---

### Post by SamNSane on 2008-10-24
I'm running 8.04 on a laptop with a 1920x1200 native resolution display.

When I'm home the unit is docked, and the monitor I use is a 1680x1050 DVI flat panel.

I set the laptop's built-in display to use that same resolution (1680x1050) so that I don't have to go into Ubuntu 8.04's screen resolution applet to change the resolution every time I start up.

But the login screen still comes up at 1920x1200. The system also insists upon using the built-in screen at login time -- whether or not I am docked. I have to opent the laptop and hit Fn-F8 to divert video to the external monitor when I'm docked.

It did NOT work that way until I started using the restricted drivers. The Open Source drivers automatically handled the different resolutions and proper use of the external monitor when docked / built-in monitor when not docked.

I've looked in /etc/X11/xorg.conf. There is no mode line and no virtual line there at all. If I try to add one the system boots into the "safe" graphical mode, and I have to reconfigure to exactly what I have now.

Does anyone know what's up with this? It's annoying that nVidia's restricted drivers should work worse for all things except 3D.

Does anyone know what to do about this? All of these threads end with information about the modes or virtual settings in xorg.conf, and the OP either says it worked or says it didn't. But none of it seems to apply to my system at all.

---

