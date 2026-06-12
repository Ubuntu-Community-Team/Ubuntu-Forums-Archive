---
title: "Limited Screen Resolution in 9.04"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by JSto on 2009-05-30
Hi,

I've been installing 9.04 on several old machines (600mhz Pentium III). I had a 17" flat panel (1280x1024) attached and everything worked fine at the native resolution and the Display preference shows all the lower resolutions as well. But when I move the same machines to the workspaces where they will be used with a 17" CRT, the highest resolution that appears is 800x600. I need 1024x768. 

I've checked various posts here and problems detecting the graphics card is often suggested as the cause, or the answers are for version 8. It seems unlikely that this could be a graphics card issue because the problem only appears when booted with a CRT. The same CRT has no problem displaying 1024x768 with Windows.

[Update: The logs show vertical and horizontal sync errors so I think the system is abandoning 1024x768 as unusable. All the posts I've been able to find that suggest how to fix this seem to apply to older versions. I edited the xorg.conf file per other instructions and rebooted. I got a message that settings were messed up and did I want to regenerate or use a backup. Regenerating got booting going again but my settings were gone (of course).

Can anyone help?

Thanks,

Jack

---

