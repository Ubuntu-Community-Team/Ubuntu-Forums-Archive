---
title: "Intel 945GM under 9.04: DVI monitor type not detected"
date: 2009-04-16
forum: Hardware
---

### Post by scgroup on 2009-04-16
I have a Dell Inspiron 9400 with the Intel 945GM controller.  I would like to use it with two external monitors, connecting one via DVI the other via VGA (the laptop LCD would remain off).  Under 9.04, gnome-display-properties shows the DVI monitor as Unknown, so one cannot select the proper resolution.

This system originally had 8.04 installed (also Win XP dual boot) and worked fine using the laptop display.  For a new application, I connected two Acer P243W 1920x1200 monitors.  Windows ran both monitors properly, but under 8.04, the VGA monitor showed only a mirror of the laptop display, and the DVI monitor remained dark.

I thought that a network upgrade to 8.10 would be a quick fix.  Although the laptop and VGA displays could now work together as a 3840x1200 virtual desktop, the DVI display was still dark.

I thought that a network upgrade to 9.04 beta might be a quick fix.  Amazingly, the DVI monitor sprang to life, but it shows as unknown.  I tried connecting an old Viewsonic VX2000 1600x1200 monitor to the DVI port; this also shows as unknown, even when the VGA port is left unconnected.  (I'm pretty sure that Windows is reading the DVI monitor characteristics correctly.  Although it won't show me the monitor name, it does give a list of resolution choices appropriate for the connected monitor.)

I tried adding a Modes "1920x1200" line to the Display subsection of xorg.conf, but this did not help.  URandR won't show the proper resolution, either.  I was unable to find a displayconfig-gtk for 9.04.

Thanks in advance for any fix or workaround suggestions.

---

