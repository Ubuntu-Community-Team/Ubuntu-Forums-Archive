---
title: "Compiz not working with Ubuntu 8.10 alternate lpia after upgrade"
date: 2009-02-13
forum: Hardware
---

### Post by vmalep on 2009-02-13
Hi everybody,

I have installed Ubuntu 8.10 alternate lpia on my Toshiba NB100 (in dual boot with the original Ubuntu Remix 8.04 and following those instructions (in French): [http://forum.hardware.fr/hfr/OrdinateursPortables/Netbooks/toshiba-netbook-austere-sujet_50126_1.htm](http://forum.hardware.fr/hfr/OrdinateursPortables/Netbooks/toshiba-netbook-austere-sujet_50126_1.htm)).

Just after the install (and if I boot with the Ubuntu 8.10 desktop live CD also), compiz was working with the 3D effects.

However, after having upgraded Ubuntu 8.10 lpia, the 3D effects stopped working.

According to the compiz-check test ([http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)), the right driver (intel) is loaded:

> Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size

I tried to replace the xorg.conf file with the one used by the life CD or the one used by the Ubuntu Remix 8.04 (this latter passes the compiz-check test, even though I cannot activate the 3D effects either): no change.

Here under is the lspci output for the display:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

I noticed that the i915 module was not loaded with Ubuntu 8.10 alternate lpia when it was with Ubuntu 8.04 Remix or the Ubuntu 8.10 live cd. I added i915 in /etc/modules and it is now loaded, but with no effect (see the attached lsmod.txt file).

Just to make sure, I have also removed all the xserver-xorg-video-* packages, except the intel one. No difference.

I have read many posts related to this issue with the 945gme video controller, but I could not find any solution. Any help would be appreciated.

Best regards,
Pierre

---

### Post by vmalep on 2009-02-13
No any suggestion?

---

