---
title: "LG W2252TQ-TF 22&quot; monitor"
date: 2008-05-02
forum: Hardware
---

### Post by sofasurfer on 2008-05-02
Has anyone used the LG W2252TQ-TF 22" monitor? Does it require special drivers or anything like that? How do you like it? I'm using Hardy 64bit.

---

### Post by teaker1s on 2008-05-02
I'm running a 32 inch lcd with vga. provided this model has vga, the only thing you may need is 
```
sudo dpkg-reconfigure xserver-xorg
``` to get the settings correct for display modes

---

### Post by Cygoku on 2008-05-02
It will find the native resolution at next start and everything will be fine.

Cygoku

---

### Post by tchalvakspam on 2008-10-06
Just got the same monitor, after a lot of fiddling with the screen resolution, it's now showing in all its 1680x1050 glory.

This is in Hardy Heron, Gnome, on a Dell Dimension C521.

My recommendation when first setting up an LG Flatron W2252TQ and probably other similar LG Flatron monitors with ubuntu is:
Make sure to install the driver (W2252QT.inf or something) from the cd that came with it, . You can install it by running sudo displayconfig-gtk on the command line to get to a gui to work with.

Restart after installing the driver, then try to change your resolution to the appropriate value (I'm using 1680x1050 right now).

If your default user's desktop doesn't adjust the first time around, use the "switch user" option to view a blank user's desktop to see if the default xorg.conf file is actually handling the new monitor and resolution fine, and it's just the current configuration that isn't adjusting. That'll at least tell you whether it's some user-specific setting or whether the default ubuntu configuration isn't handling it either.

Most important is the install of the driver, though, I think.

---

