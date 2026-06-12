---
title: "Touchpad temporarily unresponsive"
date: 2013-12-22
forum: Hardware
---

### Post by swmmng on 2013-12-22
I have xubuntu, with Ubuntu 13.10 as the core on an Asus 1215n Eee PC. Periodically, my touchpad will stop responding for 5-10 seconds. During this time, the keyboard will still work fine. After the short bit of unresponsiveness, the touchpad works fine again. Does anyone have any idea what's going on, or how to fix it?

---

### Post by Vormeph on 2013-12-22
Xubuntu has a feature which disables the touchpad while typing. There are also other options regarding a touchpad. I don't have an XFCE DE right now, but you'll most definitely find the appropriate configurations through the settings manager. Check if those touchpad settings are disrupting the touchpad. If that's not the case, then try reinstalling the xserver-xorg-input-synaptics driver for your touchpad. If that doesn't work, then your touchpad might not be working optimally, in which case that's a hardware fault.

---

### Post by swmmng on 2013-12-22
I think it is that particular setting - it seems to disable the touchpad most of the time, but not always. That is, sometimes I can, say alt-tab, and start moving the cursor immediately, other times not. Is it possible to change how long it takes for the touchpad to be re-enabled after a key is hit?

---

### Post by Vormeph on 2013-12-23
> **swmmng said:**
> Is it possible to change how long it takes for the touchpad to be re-enabled after a key is hit?

I dunno, but your best bet is to disable the setting if it bothers you.

---

