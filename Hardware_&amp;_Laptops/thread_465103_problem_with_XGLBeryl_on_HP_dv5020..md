---
title: "problem with XGL/Beryl on HP dv5020."
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by strm on 2007-06-05
Hello,
I am on an HP dv5020 laptop (amd64-turion, 1gb ram, ati radeon xpress 200m), running 32-bit ubuntu, and i recently attempted to get xgl and beryl working.

I followed the combined instructions in these threads:
[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)
[*][http://ubuntuforums.org/showthread.php?t=402937](http://ubuntuforums.org/showthread.php?t=402937)
[*][http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
[/LIST]
mostly 2nd and 3rd as I could not get fglrx-kernel to build properly following thread 1.

i've attached a screenshot of what my desktop looks like in XGL session (clearly unusable), i suspect the problem may be in the ati driver as this is the output i get from **fglrxinfo**:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

any help would be appreciated, thanks :D

---

### Post by strm on 2007-06-06
Success!
more or less ...

Installing the proprietary driver version 8.37.6 fixed the ATI driver problem, so now beryl seems to work, however I had to change the Window Decorator to GTK because otherwise the title bars of windows werent showing up.

So anyway, I enabled Desktop Effects, the window wobble works however workspaces on a cube does not. I have looked through the beryl settings manager and have not found a "bring up workspace cube" shortcut, i have read elsewhere that mouse3 (middle mouse button) brings it up, however i am on a laptop and so only have 2 mouse buttons :), so how would I go about bringing up the desktop cube?

Other than that everything seems to work, the vista-like alt-tab application switcher and etc.

Thanks.

---

### Post by Ub1476 on 2007-06-06
You can click both mouse buttons or you can press Ctrl+Alt+left mouse

(Desktop>Cube>shortcuts)

---

### Post by strm on 2007-06-06
beryl --version:
```
beryl-core 0.2.1
```

how do i install 0.2.0? do i have to force the older version from the repo?

edit:
neither both mouse buttons nor ctrl+alt+left mouse button works, and i looked in the shortcuts section, i'm not sure what unfold cube/next slide/prev slide are supposed to do, but none of them work.

---

### Post by Ub1476 on 2007-06-06
Hm, I think you can do it through Synaptic, but I don't know how.. Or you can just simply remove beryl, then reinstall.

```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
``` 

Note: this uninstalls XGL too.

Next follow this guide to install beryl and XGL (if you decided to remove XGL).

[Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

Scroll down to ..Alternate method: Using closed source FGLRX drivers from ATI.. and follow guide from there.

---

### Post by strm on 2007-06-06
i removed beryl and xgl and reinstalled them exactly as the guide you linked suggested, and i still have no cube :P

beryl --version is 0.2.0

any more ideas?

---

### Post by strm on 2007-06-06
None of the Beryl settings seem to work either, ie, I change something in the Beryl settings manager and yet nothing if affected. I cannot change themes with the emerald-theme manager either...

something is definitely not right...

---

### Post by Ub1476 on 2007-06-06
Have you chosen beryl as your windows manager?

---

### Post by strm on 2007-06-06
if i choose beryl as my window manager, my screen goes completely black with only the mouse cursor visible and mobile.

---

### Post by strm on 2007-06-06
It is finally working, the thing that fixed it was changing the Rendering Path to Texture from Pixmap in the Advanced Beryl Options.
Still a downside however, i have lost the gnome look-and-feel and instead the interfaces look more like an old version of kde. I'll assume for the time being that this is beryl's "look and feel" so i will be playing around with the settings to make it more suit my preferences, however please correct me if i am wrong.

---

