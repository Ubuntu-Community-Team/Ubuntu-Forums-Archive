---
title: "geforce 2 with compiz"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by pavolzetor on 2007-11-18
hello when i start "compiz" in terminal it's returned this ```
pk@pk-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0151 (rev a4) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```

i had not install "xserver-xgl", because when i install them 3D acceleration don't function

i have geforce 2 Ti 64 MB and Gutsy Gibbon and driver graphic card is "nvidia-glx-legacy"

---

### Post by tonyhawz on 2007-11-20
I have a TNT2 card with legacy drivers installed.
i installed "xserver-xgl", and I broke direct rendering , and of course copiz didnt work.

```
matias@chalaibrothers:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

```
matias@chalaibrothers:~$ compiz 
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

---

### Post by tonyhawz on 2007-11-20
i removed the xserver-xgl package, now i'e got direct rendering ( using the  'Option          "AllowGLXWithComposite" "True" '  workarround at xorg.conf)(legacy driver bug?)

but I need to know some things before I continue with this
is there any way to have xserver-xgl running with hardware aceleration ? (rememer my TNT2)
can someone explain me de differences between xgl and aiglx ? do they provide the same funcionalities ? which come by defaut ?
is the xserver-xgl config file xorg.conf ?

thanks

---

### Post by tonyhawz on 2007-11-22
from what I've learned reading the web about compositing and nvida-legacy drivers , is that you cannot have compiz running with an old nvidia video card.
That is because the fixes you have to add to xorg.conf in order to make your card drivers not go Segmentation fault.

correct me if I'm wrong...

---

