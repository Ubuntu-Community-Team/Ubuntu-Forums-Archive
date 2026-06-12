---
title: "Fresh install - Nvidia 6600GT - Corrupt Display"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by witchy2k1 on 2005-10-01
I've just installed the OS (5.04) but when xserver launches I cannot see the desktop as it is corrupt (colourfull verticle stripes and colourfull blocks) I cannot see any icons etc.

I went into recovery mode and entered

**SUDO DKPG-RECONFIGURE XSERVER-XORG**

Which let me autodetect and reconfigure the GFX card but when I saved the changes and restarted xserver the display was still corrupt.

Can anyone help?

---

### Post by tseliot on 2005-10-01
Boot in recovery mode and type

sudo nano /etc/X11/xorg.conf

scroll the file down (you have to use your keyboard) until you find the line with section Device and make sure the word I put in red is &#8220;vesa&#8221;:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]nv[/COLOR]"
BusID "PCI:1:0:0"


CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

Restart your computer

Then if you want to install nvidia proprietary drivers (for 3d acceleration and other features) you can follow my easy guide.

[http://ubuntuforums.org/showthread.php?t=57368]("http://ubuntuforums.org/showthread.php?t=57368")

---

