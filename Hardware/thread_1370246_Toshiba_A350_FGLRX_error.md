---
title: "Toshiba A350 FGLRX error"
date: 2010-01-02
forum: Hardware
---

### Post by Gralamin on 2010-01-02
I'm not sure if this should go here, but at any rate:
I've been trying to get fglrx working for a while (Mobility HD 3650), and just recently tried the following, from a worse working installation:
```
sudo /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo rm /etc/X11/xorg.conf
sudo shutdown -r now

sudo apt-get install xorg-driver-fglrx
aticonfig --initial -f
aticonfig --acpi-services=off
```
Which has gotten me pretty far. When my computer starts up, however, I receive an error, and am put in low graphics mode.
> (EE) fglrx(0): CAIL: CAIL_ASICSetup failed, error 1
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdatper failed
(EE) fglrx(0): PreInit failed

My xorg log can be found [here](http://pastebin.com/f70edd8fc). Anyone have any idea of how to fix this?

Edit: [xorg.conf](http://pastebin.com/m5920a089) just in case.

---

### Post by Gralamin on 2010-01-04
I'm just going to give this a bump, just in case.

---

### Post by rainwall on 2010-01-20
I have exactly the same problem,
did you find the solution brt?

---

