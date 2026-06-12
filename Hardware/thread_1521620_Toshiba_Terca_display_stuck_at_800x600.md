---
title: "Toshiba Terca display stuck at 800x600"
date: 2010-07-01
forum: Hardware
---

### Post by jjustind on 2010-07-01
Hello all, 

I recently installed Ubuntu 10.04 LTS and I've been working on a display issue for a few hours now. I've been careful enough to search the forums before I post, even so, I apologize if I'm asking a redundant question. 

I have a Toshiba Terca M1 notebook, an old one at that. Whereas installation goes well and fine, it would seem as though  the screen resolution is stuck at 800x600. 

I've gone through and attempted to edit the xorg.conf file, however, the suggested place of the file: /etc/X11/  is not where the xorg.conf file is located. Furthermore, I can't seem to find it at all. 

If I go through the GUI to change the screen resolution, the max it allows me to set is 800x600. 

Is there a way to change the screen resolution while lacking an xorg.conf file? Am I doing something silly or wrong? I most certainly appreciate any guidance anyone may offer.

---

### Post by clrg on 2010-07-01
/etc/X11/xorg.conf is no more. You can create one, and X11 will honor your settings, but it was removed with the more recent versions.

You don't have to mess around with xorg.conf though, just use xrandr.

```
xrandr
```

will show you all your displays and supported modes. Set the resolution with

```
sudo xrandr --output <screen> --mode <resolution> --primary
```

For example:

```
sudo xrandr --output VGA1 --mode 1920x1080 --primary
```

If xrandr doesn't show possible resolutions over 800x600, there might be a problem with your graphics driver. Please search the driver's page of Toshiba's website.

---

