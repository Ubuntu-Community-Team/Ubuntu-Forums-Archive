---
title: "1360x768 resolution changes after login in Kubuntu"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by phenest on 2007-02-07
I decided to buy a new 20" Toshiba widescreen LCD digital TV which doubles up as my monitor. Immediately, I encountered a problem. The TV's native resolution is 1360x768, so I installed NVIDIA's latest driver (9746) which has support for flat panel displays. Using the nVidia settings, I was able to select that resolution and all was well. Well, almost.

Originally, I was using Ubuntu with the KDE desktop installed (kde-core and NOT kde-base or kubuntu-desktop). This was working fine with my new LCD TV. I decided I preferred KDE to Gnome so I did a fresh install of Kubuntu and installed the nVidia driver on that. Firstly, the Kubuntu installation has more applets in the Control Center than in Ubuntu with kde-core installed, namely: Peripherals> Monitor & Display. This applet shows the correct monitor (Vestel 20W TFT MON) but shows nVidia GeForce FX (generic) instead of NVIDIA GeForce FX 5200 as shown in the nVidia Settings. Also, it won't give me the 1360x768 resolution.

Here's the strange bit:

When the login screen appears, it has the 1360x768 resolution. I type my password and press Enter. The resolution then changes to **1280**x768! The only way to get it back is change it via the nVidia Settings. Somehow, I have managed to stop it happening although I don't know how, but it has stopped. But questions remain:

Why would the resolution change after logging in?
Why doesn't the Control Center applet show the correct driver or resolutions?

Beats me!

BTW, the Control Center applet doesn't have the correct driver in its driver list. And I'm using Kubuntu Edgy Eft.

---

### Post by kWahab on 2007-02-08
Try modifying or deleting the following file
"/home/"USERNAME"/.kde/share/config/displayconfigrc"

worked for me on Kubuntu edgy eft.

---

### Post by phenest on 2007-02-08
Excellent! Thank you. You've no idea how frustrated I was getting (or maybe you do)! I modified it to suit the 1360x768 resolution but also to set the refresh rate to 50Hz as the 60Hz setting made the screen flicker slightly.

But why does that happen? Shouldn't the Monitor & Display applet show the correct resolutions/refresh rates etc? I don't understand why it doesn't have the correct driver listed.

---

### Post by kWahab on 2007-02-09
I guess it's a bug, the display module is unable to detect the new nvidia driver. I was happy enough to have my problem solved to think any further. :)

---

### Post by phenest on 2007-02-10
I agree. I just avoid that Control Center applet to avoid further problems.

---

### Post by mrmcd on 2007-02-20
I need to comment on this because the same bug applied to my context.

I was trying to clone output from my laptop to a second monitor with 4:3 aspect ration and made the mistake of using "System Settings / Kontrol Center / whatever it iss called in various distros".

This not only resulted in my /etc/X11/xorg.conf being overwritten, but ignored when i restored it because of "/home/"USERNAME"/.kde/share/config/displayconfigrc"

Anyone using the official NVIDIA binaries should be wary of this problem.  I have a feeling it will be more prevalent as use of beryl/compiz increases.

---

### Post by phenest on 2007-03-03
I installed a couple of updates 2 days ago, one of which was for nVidia. Without thinking, I installed it and the X server refused to start. I re-installed nVidia's driver and all was well except the original problem is re-occuring. In fact, it now happens when the login screen appears. But the nVidia splash screen is correct. The displayconfigrc file shows the 1360x768 resolution from when I first fixed it. I even deleted it, but to no avail.

---

### Post by phenest on 2007-03-03
Not to worry. Silly me didn't reconfigure the xorg.conf file. All is well now.

---

