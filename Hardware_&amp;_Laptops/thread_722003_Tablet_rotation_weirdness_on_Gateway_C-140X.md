---
title: "Tablet rotation weirdness on Gateway C-140X"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by Cherry Cotton on 2008-03-11
Thanks to the efforts of a kind developer at AMD, I'm now able to use the open-source "radeon" driver for my Gateway C-140x tablet, which has an ATI Radeon 2300HD card for its graphics. Before, I was confined to the proprietary train-wreck "fglrx" and the newcomer "radeonhd," neither of which feature rotation support.

I'm happy to say I now have rotation... "working" with major caveats.

1. The bottom part of the screen (following rotation) is completely blank. GNOME acts as though there is the extra height, but I cannot see it because it is now covered by blackness. I can move my cursor down there and still see it, but I cannot drag windows down there or anything like that. It's just empty, graphically... I don't get it. (I can click on menus and such down there, and if they are tall enough, they will peek above the blackness. That's all I see.)

2. The lag is unbearable! I'm not sure why this happens. Windows leave trails as I drag them, and scrolling is choppy. It's possible that residue from fglrx is preventing the "radeon" driver from taking control of the direct-rendering interface. For instance, when I want to activate Compiz (yes, I get this kind of sluggishness using _Metacity!_), I get these errors (once the appearance properties window appears, I choose "desktop effects," then "normal"):

```
tina@PolymascotfoamalateSpoon:~$ gnome-appearance-properties 
WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

There is no available graphics driver for your system which supports the composite extension.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7211 (rev ce) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: line 400: /usr/local/bin/compiz: No such file or directory
```

It talks about "fglrx," but I'm not using it anymore! :( However, I've heard that "fglrx" can leave these kinds of problems in the wake of its power-hungry MADNESS.

Of course, I don't know if either of these problems are related to direct rendering or anything like that. It's just a guess.

Any help would be greatly appreciated! I've been suffering for months under the evil regime of the landscape orientation. Please help me break free! Thank you!

---

### Post by Cherry Cotton on 2008-03-13
Updates on this issue!

Ignore #2 in the previous post. It's nonsense! I was totally wrong about what the problem was. I needed "EXA" acceleration, which let the hardware do the rotation stuff rather than software. Now, the lag is totally gone. Whoo!

The only problem left is the weird half-blank screen. Does that sound familiar to anybody? Could somebody help me out.... pweeeease?

Thank you!

---

### Post by CAsurfer on 2008-04-08
I got rotation to work with other major caveats in Hardy beta. Here's the guide I wrote: [http://ubuntuforums.org/showthread.php?p=4680284](http://ubuntuforums.org/showthread.php?p=4680284)

---

