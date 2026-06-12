---
title: "Compiz settings fail"
date: 2008-09-18
forum: General Help
---

### Post by justinblat on 2008-09-18
I am running a fully updated installation of Hardy Heron, and trying to enable compiz on my system.  In the appearance preferences, the default of 'none' is selected for visual effects.  When I change this to 'normal', the screen flashes, and comes back.  I click OK, but nothing seems different.  The next time I enter the tool, the 'none' radio button is again selected.  I attempted to run gnome-appearance-properties to check output:


There is no available graphics driver for your system which supports the composite extension.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Aborted

(gnome-appearance-properties:6438): GLib-CRITICAL **: g_array_free: assertion `array' failed

(gnome-appearance-properties:6438): GLib-CRITICAL **: g_array_free: assertion `array' failed

Google was not terribly helpful with any snippets of these errors.  Trying to install xgl server led to a new inability to log in, and a few lost hours.  I am using a GeForce 5200 FX. and I have the proprietary drivers enabled.  I have removed and re-installed compiz, and attempted just running the compiz --replace command.  This returns very similar output to above.

Any ideas out there?

---

