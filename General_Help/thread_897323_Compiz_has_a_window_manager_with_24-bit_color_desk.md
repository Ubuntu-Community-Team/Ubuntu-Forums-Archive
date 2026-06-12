---
title: "Compiz has a window manager with 24-bit color desktop, but NOT with 16-bit"
date: 2008-08-22
forum: General Help
---

### Post by benjamin222 on 2008-08-22
Hey, after days of messing with Compiz and having full screen opengl issues, I finally got Compiz to the point where I'm able to run it alongside fullscreen opengl apps, but I have to run my desktop at 16-bit color. Not really a big deal, I hardly even notice the color depth unless I'm dealing with imaging, but with 16-bit desktop color there is no window manager!! No minimize, maximize, close, title bar, and no ability to move around windows. Under 24-bit there is a window manager... So how can I fix this so there either IS a window manager at 16-bit or full screen opengl apps work at 24-bit!?? Any help will result in a huge virtual hug (we'll just hug our monitors at the same time it will be awesome)

---

### Post by eightmillion on 2008-08-22
OpenGL apps don't run so swell for me either with compiz running. What I did was installed fusion-icon. > sudo apt-get install fusion-icon It's a little application that sits in your system tray. When you want to run an OpenGL application you can just right click on it and select *Select Window Manager>Metacity* . Then when you exit out of the OpenGL application you just select compiz.

---

### Post by benjamin222 on 2008-08-22
Yeah I've installed the compiz icon and thats what I've been doing for the time being. Just seems like there must be a simple solution out there that I'm just not finding.

---

### Post by xiphosurus on 2008-11-04
bump. i have the same problem since upgrading to intrepid. running compiz at 16-bit gives a bunch of errors, which results in the window manager not showing up. when i then try to run gtk-window-decorator, it tells me a decorator is already running. running at 24-bit is fine (but slow... so i prefer 16 bit).

well, not to hijack, but 24-bit might be fast enough if only i can get direct rendering enabled for compiz. right now, dri is enabled (giving me abt 1400fps in glxgears), but compiz always switches it off for its own process (resulting in about 700fps). after starting compiz, i get this...

~$ glxinfo |grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

computer is thinkpad t40 with radeon 9000.

---

### Post by nkrick on 2008-11-12
I am experiencing the same problem.  At 24-bit color compiz works but performance is too slow to be usable (Radeon M9000).  At 16-bit color window decorations are missing and other 3d effects are also broken causing issues such as a plain white terminal screen.  Compiz with 16-bit color worked fine in Hardy (and Gutsy, Feisty, and Edgy).

Has anyone come up with a solution to this problem?  I would like to use compiz in Intrepid.

---

### Post by el_Nacho on 2008-11-21
i had to use 16  bit more for performance reasons with my onboard graphics. before i used 16 bit mode the system was slow but eighter with and without compiz.

i guess if it worked with the last version and some people experiencing problems someone got to fix it sometime.

---

### Post by Mohonri on 2009-02-27
I have the same issue.  Same video hardware (Mobility Radeon 9000/RV250).  Using the radeon driver and at 1400x1050x24-bit color, compiz runs very slowly.  Dropping the resolution improves performance, as does dropping the color depth to 16-bit.  However, with 16-bit, all the window decorations disappear, as well as some windows' contents.

Running at a lower resolution isn't acceptable, because 1400x1050 is the native resolution on my laptop.  Any help would be much appreciated.

This hardware (RV250) kinda got caught in limbo--the open-source driver isn't up to snuff yet performance-wise, and the proprietary driver doesn't support it any more.

---

