---
title: "Almost no image on external monitor"
date: 2009-07-05
forum: Hardware
---

### Post by wacky_keyboards on 2009-07-05
I have a problem with an external monitor that is connected
to my laptop via an HDMI-to-HDMI connector.  When I am logged
in under Ubuntu, I am unable to switch to the external
monitor, either displaying on the external monitor alone or
in concert with my laptop's display (either in "mirror" mode
or "multi-screen" mode).  When I try to enable display on
the external monitor, either through a Function-hotkey combo
or through System->Preferences->Display, the external monitor
remains dark, except for occasional flickerings showing what
should be displayed (e.g. a copy of my laptop's display's
contents if I've enabled "mirror" mode).

However, I have verified that this is something which is
(probably) linked to the X server settings which are enabled
once GDM is active.  This is because I have booted up the
laptop with the external monitor already connected, and I
can see all the display contents from boot-up until the login
prompt (when the external display goes mostly-dark).  That is,
I see on both the laptop display and the external monitor the
dual-boot prompt from GRUB, I see the initial text messages
from the Ubuntu boot, and I see the Ubuntu booting graphic
image with the "moving bar" underneath.  However, as soon as
the login screen is activated, the external monitor goes
mostly-dark (though there is no problem with the laptop's
display).

In addition, I have booted into Windows Vista, and confirmed
that I can switch between the laptop display and the external
monitor, and also have both active, either in "mirror" mode
or "multi-screen" mode, with no trouble.  (I also have a second
laptop which has no trouble with the external monitor.)

It seems that there's a configuration problem, but my initial
search on the web proved fruitless (most likely because I did
not use the best search keywords).  Any help that could be
provided would be most appreciated!

Thanks!

P.S.  here is my system configuration:

OS:  Ubuntu 9.04 (Jaunty Jackalope), with Windows Vista (dual-boot)
Last system update:  2009 Jul 05 (approximately 15:30 PDT)

Laptop:  Alienware M17
Graphics:  M17/M15X ATI Radeon M88 XT 512MB HD3870 Master Rev 1
External monitor:  Hanns-G HG281 (28" TFT LCD)

---

