---
title: "display issues with jaunty on ibm x30"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by elliah on 2009-04-28
i just upgraded from xubuntu 8.10 to 9.04 using the update manager...everything seems to work fine in terms of sound, networking and scim inputs and the like, but display has a few issues.
parts of the taskbar, like 'places' or my icon shortcuts tend to disappear but will reappear when my mouse hovers over it. also, while i was typing this thread some parts of it flashed in and out as i typed. 
the same issue applies for the bottom taskbar, where my trash icon and workspaces also flash or disappear/reappear.
my background also does not render correctly, with fuzzy lines running across the screen. my menu bar is not one solid colour but half grayed out. changing themes results in either fuzzy lines or multiple x's.
also, i'm not sure if this is a side effect of upgrading instead of a clean install but i have two instances of help, screensaver, image viewer, dictionary installed. can i remove them?
thanks for any help.
i'm using an ibm x30 with 512mb of ram. and graphics are Intel 830 "Extreme Graphics"(Intel Corporation 82830 CGC [Chipset Graphics Controller]

---

### Post by elliah on 2009-04-28
i've trolled a few forums and found some people advising setting colour depth the 16bit to deal with display corruption issues but my xorg.conf shows:

Section "Device"
          Identifier      "Configured Video Device"
EndSection

and no colour depth option at all.

---

### Post by andthen.. on 2009-10-07
I have exactly the same problem! I installed xubuntu 9.04 on my x30 and like you say about the disappearing reappearing icons and all the rest.

Please does anyone have any advice?

---

