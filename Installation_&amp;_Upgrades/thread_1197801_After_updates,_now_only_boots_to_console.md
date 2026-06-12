---
title: "After updates, now only boots to console"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by jnah on 2009-06-26
Hi all,

Using Jaunty, have been since it came out (plus various version prior, all upgraded rather than new installs), no problems. However, a recently installed update required me to restart the PC (A new kernel version I presume). On restart, the usual splash screen appears, the graphical progress bar gets to 100%, then the boot drops to a text console login. If I log in, then sudo reboot, its says gnome shutting down, which implies its running, but no GUI.

If I use grub to boot to the previous kernel version, all is fine.

There is a message on the login console saying a failed USB enumeration of some description, on port 4, but booting to the previous kernel where the GUI works shows nothing on port 4.

Machine spec. Ancient Athlon 2000XP, 1.5GB RAM, NVidia based graphics card (using the proprietry NVidia drivers), two (2) PCI USB extension cards, plus various USB devies (Wireless, Bluetooth, Card reader, USB external drive)

Any ideas?

---

### Post by jnah on 2009-06-27
Seems to be quite a few people suffering with boot failures after this kernel update - seemingly with different failure modes, but as yet, no-one seems to have an answer.

Does anyone have the faintest idea what I can do to sort this out?

---

