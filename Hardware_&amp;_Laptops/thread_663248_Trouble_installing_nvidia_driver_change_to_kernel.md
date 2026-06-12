---
title: "Trouble installing nvidia driver change to kernel"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by pxrox on 2008-01-09
Changed from 2.6.22-14-generic to 2.6.22-14-386 to try to fix slow graphics, following suggestions in the forum (Thread " VERY slow laptop with Ubuntu?").

(Tried ENVY, but got python error after apparently successful installation:
>sudo envy -g
Traceback (most recent call last):
  File "/usr/share/envy/gtkenvy.py", line 7, in ?
    from Envy import objects
ImportError: No module named Envy
)

So, instead followed Track 1 instructions found here:
     [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#REQUIREMENTS](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#REQUIREMENTS)
apt-get install nvidia-glx
etc....

Now, unclear that nvidia driver installation has worked, in that:
 *No nvidia splash screen
 *800x600 Xwindow instead of full screen
 *System>Admin>Restricted Drivers says that the nvidia driver is there & enabled, but doesn't seem to be used.
 *System>Admin>Screen&GraphicsPrefs shows only generic nvidia driver; if I choose this, lose the screen entirely (even console) and have to hit the power button to reboot.

Reboot & GRUB selection of generic kernel gets me back to full screen mode, but again no nvidia splash screen anymore. Here, System>Admin>Screen&GraphicsPrefs says I'm at 1600x1200/50Hz, with nvidia driver; card identified as GeForce2 DDR (generic).

Running Gusty Gibbon 7.10 (I'm brand new to ubuntu; system first loaded up 1-Dec-2007), on Dell Latitude C810, GeForce2 Go (32 MB) (as reported by lspci).

Suggestions, please!

---

