---
title: "Screen resolution is unchangeable/display not recognized"
date: 2008-10-19
forum: General Help
---

### Post by jwwadk on 2008-10-19
OK, so I recognize that I may very well be the stupidest person on the face of the planet, since I was trying to hook up an external display to my Asus M50sv-A1 laptop, and I somehow changed the settings (using the nvidia X Server settings program) so that my screen resolution is now fixed at 800x600 and nothing will recognize my display. I suspect that my xorg.conf file is to blame for this. I did get to a point where Ubuntu (8.04) started up in low-graphics mode, and I had to select a display type and driver. It recognized a "Plug 'n' Play" device, and I selected the nvidia driver from the list it gave me. Ubuntu then started up in the mode it is currently in. I have lost all of my compiz settings, but I don't mind that so much as the fact that my screen is not recognized. Is there any way to fix this? I still have all of my files, thankfully, but I would like to be able to use Ubuntu in it's prior configuration. I was dumb enough not to back up xorg.conf, sadly. Is there any way to restore all of my machine's original settings to the point they were at when I installed Ubuntu without changing my files? Any help would be greatly appreciated. 

Thanks.

---

### Post by anystupidname on 2008-10-19
Try

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.borked
sudo dpkg-reconfigure -phigh xserver-xorg
```

And reboot. If that doesn't change anything, lets see a copy of the xorg.conf

---

