---
title: "Dual GPUs and GLX"
date: 2012-01-23
forum: Hardware
---

### Post by ForgivenByJC on 2012-01-23
My previous old motherboard died on me and I had to replace it.  I have been trying to sort this out for two weeks now, with little success. :confused:
**The setup:**
[LIST]
[*]Intel HD 3000
[LIST]
[*]No Component nor S-Video out
[/LIST]
[*]Gigabyte GeForce 7600GT (previous video card)
[*]19" LCD (DVI)
[*]32" Flat CRT
[LIST]
[*]Component, composite, S-Video, coax input ports
[*]No VGA, DVI, nor HDMI input ports
[/LIST]
[/LIST]
**The objective:**
Hook the 19" LCD to the onboard (Intel HD 3000) DVI.  Hook the 32" CRT to the discrete GPU (7600GT) with S-Video.  Because of the Intel HD 3000, I had to upgrade from Ubuntu 10.04 LTS to 11.10 (no LTS :().  With my previous system the 7600GT was operating both the 19" and 32", with the 32" being for mythtv frontend.
**Current outcome:**
The 19" and 32" work but drivers seem to be a problem.  When setup with "ServerLayout" in xorg.conf, the layout works but there is no glx support.  The 32" can work by itself with glx if the "ModulePath" "/usr/lib/nvidia-current,/usr/lib/xorg/modules" is added.  However, the 19" does not have glx with "ModulePath" "/usr/lib/nvidia-current,/usr/lib/xorg/modules", but does with just "/usr/lib/xorg/modules".  It seems the glx for the 7600GT works for itself, but not the HD 3000.  The reverse is also true, the glx for the HD 3000 works for itself, but not the 7600GT.
**The inquiry:**
Is there a way to get both GPUs working together?

This is a continuation from my previous topic [Dual GPUs and UEFI]("ubuntuforums.org/showthread.php?p=11615479"), but I have a different question so I decided to start a different topic.  Thanks! :)

---

### Post by ForgivenByJC on 2012-01-31
Bump.  Still no solution yet.  Please help.

---

### Post by ForgivenByJC on 2012-04-01
Bump, still not working.

---

