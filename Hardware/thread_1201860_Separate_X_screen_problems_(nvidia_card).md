---
title: "Separate X screen problems (nvidia card)"
date: 2009-07-01
forum: Hardware
---

### Post by enduser000 on 2009-07-01
Hello,
    I'm having problems getting a samsung 19" monitor to work on my laptop (dell xps m1330).  I have an nvidia GS8400 card and the nvidia-glx-180 package installed (restricted drivers). I'm using the Option "Rotate" "CCW" but it gives me similar results when I leave it at the normal rotation.  There are screenshots below and here's when I've done so far:

Removed /etc/X11/xorg.conf and replaced with "sudo nvidia-xconfig"

Restarted X "sudo /etc/init.d/gdm restart"

Edited the settings both with a text editor "sudo gedit /etc/X11/xorg.conf" and with the settings editor "sudo nvidia-settings"

In the screen shots it shows that the bottom half of the screen is accessible with the mouse, but not any windows.  windows spawn in the middle of the small portion where they can move.  I can also minimize windows and click where they would go (in the panel) and it'll maximize them.

Twinview works fine so I don't think it's a hardware problem.

Sometimes the windows don't refresh correctly (in one of the screenshots, that's a new nautilus window)

Any ideas?

enduser000

---

### Post by enduser000 on 2009-07-08
No one knows? I've tried many things, and been all over IRC. This worked before, and seems like it should work.  Any help is appreciated,

enduser

---

### Post by enduser000 on 2009-07-18
bump, still having the same issue with separate x screens.  Here is another screenshot,

enduser

---

### Post by enduser000 on 2009-07-19
Alright,
        I have it sort of working.  I installed the 185 nvidia driver from their site and am still having these issues:
    applications open on the wrong screen unless run from alt+f2 (I've heard this is common)

    emerald only themes my main monitor and alt+f2 > "emerald --replace" doesn't run it there

    cannot change the number of workspaces (2 is fine, but it'd be nice to have 4).  when I right click on the gnome panel workspace switcher, it opens (no matter on what monitor) with control of the workspaces on my main monitor

    my mouse would not move to the external monitor at first, after running a script from here: [http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils](http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils) my mouse will run off the left side, but not the right (like it should).  I thought this was because of the positioning of the monitors, but I don't know how to switch it in xorg.conf (didn't work from nvidia-settings)

If anyone knows fixes for any of these that'd be great, thanks,

enduser

---

