---
title: "Acer Aspire 5002WLMi"
date: 2009-05-10
forum: Hardware
---

### Post by drbobb on 2009-05-10
Hello

unfortunately this laptop, though barely 4 years old, is already obsolete. My finding is that Hardy Heron is, and will likely remain, the last version to support this hardware.

The top problem is the SiS integrated VGA, which identifies as:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

On a fresh Ubuntu Jaunty install you will find that the display comes up in weird sparkling psychedelic colors. With Kubuntu (kdm) you will find the additional problem that the X server dies at logout and is not (by default) restarted by the display manager, leaving the user at a text mode login. The latter problem can be worked around with a kdm option - but in any case, the default graphics config is unusable.

After 2 weeks or so of on-and-off searching, experimenting, multiple system hangs and freezes and a couple reinstalls (thank you, JFS, for a corrupt filesystem that was not fixable by jfs_fsck, although it did mark it as clean but the kernel code disagreed and chose to panic) -- I found there is one single workaround that (sort-of) Works For Me. To be sure, the performance is seriously degraded compared to Hardy's version of X.org -- by the frequent appearing of display artifacts (mostly flashing horizontal lines caused by display activity, like fast scrolling a window). Of course, forget about 3D acceleration (desktop effects, 3D games, Google Earth etc.) which never worked on this family of chips anyway. But 2D graphics, including fullscreen video playback, worked reasonably well up to and including Hardy.

OK so here's the deal: use the kernel framebuffer driver (sisfb), make sure it sets the display mode to your lcd's native resolution and the color depth you want (1280x800-32 in my case), and run the xserver with the **fbdev** driver (yes, **not the sis driver**). This reduces the sparkling artefacts to a reasonable level (with the sis driver you'll have it much worse) and seems to stop the frequent hangs and crashes you'll have with other combinations.

AFAICS do not expect problems with those SiS chips to be fixed in the future, they will rather get worse because I don't think there exist any developers interested in fixing them (the lone author of both the sisfb kernel modules and X.org's sis driver seems to have not touched the code in years).

OTOH the Broadcom WIFI chip ( Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)) has been mostly working in Hardy and still works in Jaunty. It does tend to act up every once in a while and refuse to maintain a connection for apparently no good reason, but a little patience and voodoo (rebooting, power-cycling, maybe power-cycling the AP) restores it to normal after a while, and you may see it work fine for weeks until it decides it's time to act up again. BTW this happened to me under windows XP too (until i purged it from my drive). Yes, this laptop is built out of crap.

**So if you own one of these machines, or another with a VGA chip from this series, and are interested in running Linux, consider getting rid of it ASAP and replacing it with something else.**

---

### Post by drbobb on 2009-05-17
Oh and let me add that while the workaround I described is OK for working with data, office documents etc, video playback is no good at all, lots of skipping esp. in fullscreen mode.

---

