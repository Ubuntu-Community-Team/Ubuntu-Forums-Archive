---
title: "Can both xgl and nvidia X server be run at the same time?"
date: 2008-08-22
forum: Hardware
---

### Post by Animeniac on 2008-08-22
I've always used envy to download and install the drivers for my Nvidia GeForce4 MX graphics card. Whenever the Nvidia graphics driver is in use, I can't use compiz (desktop effects) at a resolution higher than 1024 x 768 pixels (that resolution is too low for my tastes) - if I do, I won't get any visual desktop effects (not even the effects on the top bar of windows - instead, the top bar is disappeared). Whenever I download and install 'xserver-xgl' from synaptic, I can use compiz at a resolution higher than 1024 x 768, but I have no screensaver when the computer is idle for the time it is set in the screensaver settings (10 minutes, that is) - instead, all I get is a black screen. Also when I have xgl installed, I am unable to access all the options in 'NVIDIA X Server Settings', including resolution, and I get an error message that has "You appear to be not running the NVIDIA X Server"; and I'm not able to change the resolution in *System --> Preferences --> Screen Resolution*.

I have re-installed Ubuntu and now I don't want to just install 'xserver-xgl' from synaptic. Is it possible to have 'NVIDIA X Server Settings', Screensavers, compiz and a resolution higher than 1024 x 768 work right at the same time (on a computer using the Nvidia GeForce4 MX graphics card)? If so, what is the solution? Thanks.

---

### Post by Animeniac on 2008-08-23
Helloooo.......

I have tried the 'compiz --replace' command in Terminal, and I see all these errors:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0185 (rev c1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
```

---

