---
title: "Xorg fails to start after upgrade 15.04 -&gt; 15.10"
date: 2015-10-27
forum: Hardware
---

### Post by CoolEsza on 2015-10-27
Dear community,
I am near to crying with my Acer Travelmate (TMB115-MP-C2TQ) that annoys me ever since  I installed an Ubuntu system on it and hope for some help here:

My newest problem is a complete failure of the Xorg giving an unresponsive TTY1 screen (Basically its only the screen of the tty1 -flickering, Ctrl+Alt+F1 gives the responsive tty1)

Other kernels do the same thing, failsafeX without effect.

  Xorg.1.log shows no errors, the others (2-5) do

The first error message is 
(EE) intel(0): [drm] failed to set interface version: Permission denied [13]
(EE) intel(0): Failed to claim DRM device.
(II) UnloadModule "intel"
(EE) Screen(s) found, but none have a usable configuration.

  here is a link with all the Xorg.?.log logs and a lspci -vv output 

  [http://cloud.alexanderkulesza.de/owncloud/index.php/s/8gxc08CMEnX3wlP](http://cloud.alexanderkulesza.de/owncloud/index.php/s/8gxc08CMEnX3wlP)

  Any help will be greatly appreciated, i have no clue whatsoever.
Thanks very much in advance! 
Alex

---

